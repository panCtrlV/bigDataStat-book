# Examples

---

The examples are run on Purdue's Hathi cluster.

**Note** This example is based on the Linkage example from Advanced Analytics with Spark p37.

- **Download raw data and save on HDFS**

```bash  
# Download, process and save raw data in HDFS
panc@hathi ~$ hdfs dfs -mkdir /user/panc/linkage
panc@hathi ~$ cd download
panc@hathi download$ wget https://archive.ics.uci.edu/ml/machine-learning-databases/00210/donation.zip
panc@hathi download$ unzip -d donation donation.zip
panc@hathi download$ cd donation 
panc@hathi donation$ for i in `seq 1 10`; do 
  unzip -d block_$i block_$i.zip | hdfs dfs -put ./block_$i/block_$i.csv /user/panc/linkage 
done

# Check data are saved in HDFS
panc@hathi ~$ hdfs dfs -ls /user/panc/linkage
```

- **Bring data into SparkR**

```bash
# Hathi specific loading
panc@hathi ~$ source /etc/default/hadoop
panc@hathi ~$ module load r
########################
# Start SparkR console #
# with sparkR script   #
########################
panc@hathi ~$ sparkR --master yarn-client --packages com.databricks:spark-csv_2.10:1.3.0
```

By using `sparkR` command, `SparkR` package is automatically sourced in R and `sc` and `sqlContext` are created.

Alternatively, we can lauch SparR from within an existing R session.

```r
# $SPARK_HOME is set already
# Load SparkR library
library(SparkR, lib.loc = c(file.path(Sys.getenv("SPARK_HOME"), "R", "lib")))
# Create sc and sqlContext
sc <- sparkR.init(master = "yarn-client", 
                  sparkEnvir = list(spark.driver.memory="2g"),
                  sparkPackages="com.databricks:spark-csv_2.10:1.3.0")
sqlContext <- sparkRSQL.init(sc)
```

**Note** `com.databricks:spark-csv_2.10:1.3.0` is the package including data source connectors for popular file formats like CSV and Avro. 

**Note** [SparkR doc](https://spark.apache.org/docs/latest/sparkr.html#from-data-sources) says we should use `com.databricks:spark-csv_2.11:1.0.3` (or `com.databricks:spark-csv_2.10:1.0.3`) but I failed to load data by using this package. Instead, I use `com.databricks:spark-csv_2.10:1.3.0` and successfully loaded data. This solution is described on [this spark-csv issue page](https://github.com/databricks/spark-csv/issues/206#issuecomment-197403908).

The data set consists of 10 block files (.csv format). Let's first have a taste of the data by exlporing one piece.

```r
# Read one piece of the dataset as SparkR DataFrame
# SparkR natively support .csv file format
# By default, `read.df` reads data from HDFS.
rawblock1 = read.df(sqlContext, "/user/panc/linkage/block_1.csv", "com.databricks.spark.csv", header="true") 

head(rawblock1) # how it looks like
printSchema(rawblock1) # schema shows data types
head(select(rawblock1, rawblock1$id_1)) # select one column
class(rawblock1) # DataFrame
nrow(rawblock1) # 574913
ncol(rawblock1) # 12

# Another piece of the dataset
rawblock2 = read.df(sqlContext, "/user/panc/linkage/block_2.csv", "com.databricks.spark.csv", header="true") 

nrow(rawblock2) # 574913

# Combine the two DataFrames
bigrawblock = SparkR::rbind(rawblock1, rawblock2)

nrow(bigrawblock) # 1149826
```

Now, let's "bring" all data into SparkR.

```r
###########################################
# If you know there is no missing values. #
###########################################
# Define the schema
# otherwise, spark-csv will not infer the column types
# and set all columns as String
myschema = structType(structField("id_1", "integer"),
                      structField("id_2", "integer"),
                      structField("cmp_fname_c1", "double"),
                      structField("cmp_fname_c2", "double"),
                      structField("cmp_lname_c1", "double"),
                      structField("cmp_lname_c2", "double"),
                      structField("cmp_sex", "double"),
                      structField("cmp_bd", "double"),
                      structField("cmp_bm", "double"),
                      structField("cmp_by", "double"),
                      structField("cmp_plz", "double"),
                      structField("is_match", "boolean"))

# first piece
rawblock = read.df(sqlContext, "/user/panc/linkage/block_1.csv", "com.databricks.spark.csv", header="true", schema=myschema) 
# total number of pieces
nblocks = 10
# combine all pieces
for(i in 2:nblocks){
  data_file_path = paste("/user/panc/linkage/block_", i, ".csv", sep='')
  rawblock_i = read.df(sqlContext, data_file_path, "com.databricks.spark.csv", header="true", schema=myschema) 
  rawblock = SparkR::rbind(rawblock, rawblock_i)
}

################################
# If there are missing vlaues, #
# use default schema.          #
################################
# first piece
rawblock = read.df(sqlContext, "/user/panc/linkage/block_1.csv", "com.databricks.spark.csv", header="true") 

#rawblock_filter = filter(rawblock, rawblock$id_1=="16024"&rawblock$id_2=="27196")
#collect(rawblock_filter)

# total number of pieces
nblocks = 10
# combine all pieces
for(i in 2:nblocks){
  data_file_path = paste("/user/panc/linkage/block_", i, ".csv", sep='')
  rawblock_i = read.df(sqlContext, data_file_path, "com.databricks.spark.csv", header="true") 
  rawblock = SparkR::rbind(rawblock, rawblock_i)
}
# Cast column types one-by-one
rawblock$id_1 = SparkR::cast(rawblock$id_1, "int")
rawblock$id_2 = SparkR::cast(rawblock$id_2, "int")
rawblock$cmp_fname_c1 = SparkR::cast(rawblock$cmp_fname_c1, "double")
rawblock$cmp_fname_c2 = SparkR::cast(rawblock$cmp_fname_c2, "double")
rawblock$cmp_lname_c1 = SparkR::cast(rawblock$cmp_lname_c1, "double")
rawblock$cmp_lname_c2 = SparkR::cast(rawblock$cmp_lname_c2, "double")
rawblock$cmp_sex = SparkR::cast(rawblock$cmp_sex, "double")
rawblock$cmp_bd = SparkR::cast(rawblock$cmp_bd, "double")
rawblock$cmp_bm = SparkR::cast(rawblock$cmp_bm, "double")
rawblock$cmp_by = SparkR::cast(rawblock$cmp_by, "double")
rawblock$cmp_plz = SparkR::cast(rawblock$cmp_plz, "double")
#rawblock$is_match = cast(rawblock$is_match, "bool") # bool type doesn't handle "?" missing values

#rawblock_filter = filter(rawblock, rawblock$id_1==16024&rawblock$id_2==27196)
#collect(rawblock_filter)

# Persist data
persist(rawblock, "MEMORY_AND_DISK")

# Check if all data are available
nrow(rawblock) # 5749132 
printSchema(rawblock)
```

**Note** I couldn't find SparkR's native support for read data files (at least .csv files) from a folder. 

**Note** We can see `spark-csv` sets column types to String by default and will not attempt to infer types. So we need to cast each column to their proper data types in the second method above. [Here](https://mail-archives.apache.org/mod_mbox/spark-dev/201506.mbox/%3CCAKx7Bf8c19Bsdeihqm5Xu=ZnzCJ3J8BJotdru4Z3VvEhdC3=4w@mail.gmail.com%3E) is an Apache mailing list on this matter.

**Note** According to [Spark SQL, DataFrames and Datasets Guide](http://spark.apache.org/docs/latest/sql-programming-guide.html#data-types), 

>There is specially handling for not-a-number (NaN) when dealing with float or double types that does not exactly match standard floating point semantics.

  If a column contains "TRUE", "FALSE" and missing values represented by "?" and we want to cast it to "bool", SparkR fails to gracefully accommodate the missing values and <font color='red'>fuck up</font> the whole column. That's why I left the last column unchnaged.

- **Exploring Data**

  **Aggregating** (bar graph)

  ```r
  # Count the number of "TRUE" and "FALSE" respectively.
  # Similar to Spark’s countByValue action.
  grouped = groupBy(rawblock, "is_match") # GroupedData class
  grouped_count = count(grouped)
  collect(grouped_count)
  ```

  **Note** We aren't able to do much with the GroupedData at this point - we can't print or view the data. The only way to use the GroupedData is to pass it into aggregate functions, such as agg or avg.

  **Note** Performing aggregations on data in the cluster is usually expensive. The more filtering that we can do to the data before performing an aggregation, the faster we will get an answer to our question.[^filter_before_aggregate]

  **Summary statistics**

  ```r
  library(dplyr)

  # remove missing values for one column
  filter(rawblock, isNotNull(rawblock$cmp_fname_c2)) %>% head()
  ```

  **Note** If you are using the latest version of R, follow [this page](https://cran.r-project.org/web/packages/dplyr/README.html) to install `dplyr` package. Otherwise, you may need to install it from source (including any dependencies) by downloading a proper version (recommend >=0.4) from [cran archive](https://cran.r-project.org/src/contrib/Archive/dplyr/) and call `install.packages("path/to/download/file", type="source", repo=NULL)`.

---

[^filter_before_aggregate]: Advanced Analytics with Spark p42