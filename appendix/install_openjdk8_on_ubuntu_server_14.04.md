# Install OpenJDK 8 on Ubuntu Server 14.04[^install_openjdk8_ref]

OpenJDK 8 was released in March 2014. It is available in Ubuntu Software Center for Ubuntu 14.10 and Ubuntu 15.04 but not for Ubuntu 14.04. This tutorial teaches you how to install OpenJDK 8 from a PPA repository[^what_is_ppa](there are other methods).

- **Step 1** Add the PPA by running the following command. Type in user password when it asks and hit Enter to continue.
  
  ```bash
  sudo add-apt-repository ppa:openjdk-r/ppa
  ```

- **Step 2** Update system package cache and install OpenJDK 8.

  ```bash
  sudo apt-get update 
  sudo apt-get install openjdk-8-jdk
  ```

- **Step 3** (Optional) If you have more than one Java versions installed on your system. Run below command set the default Java:

  ```bash
  sudo update-alternatives --config java
  ```

---

[^install_openjdk8_ref]: This tutorial is copied from the post at  [http://ubuntuhandbook.org/index.php/2015/01/install-openjdk-8-ubuntu-14-04-12-04-lts/](http://ubuntuhandbook.org/index.php/2015/01/install-openjdk-8-ubuntu-14-04-12-04-lts/)

[^what_is_pps]: PPA stands for Personal Package Archives, they are for non standard software/updates. If you are interested in more details about PPA, [the ask ubuntu page](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them/4987) is a good start. 