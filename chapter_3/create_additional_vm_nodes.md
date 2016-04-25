## 2. Creating Additional Virtual Machine Nodes

We have created a VM as the front end of our cluster. In this section, we will create two more VM nodes so that the three nodes can be connected to form a virtual cluster. The following figure shows the diagram[^cluster_diagram_source] of the desired cluster. 

![Diagram of a cluster with three VM nodes.](../figures/vm_cluster_three_nodes_diagram.png)

[^cluster_diagram_source]: This diagram is adapted from the one on [https://www.communigate.com/communigatepro/ClusterStatic.html](https://www.communigate.com/communigatepro/ClusterStatic.html).

### 2.1. Further Configuration on the Front End as a Base System

While "fe1" is going to be our front end, it can be configured as the base system for the other two nodes. VirtualBox allows us to create a node by cloning an existing one so that we don't have to build the other two nodes from scratch. We have done most of the work in the previous section. Some additional configuration, in particular some networking setting, is needed to accommodate the multi-node cluster environment.

- Add additional hostnames of the other two nodes in `\etc\hosts` file. 