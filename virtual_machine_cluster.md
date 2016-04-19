# Virtual Machine Cluster

Cluster can be very expensive to build. It consists of many computer nodes, network switches, internet cable and other hardware equipments. It also requires installation of operating systems and managment softwares to be functioning. Dedicated administrating staff are also needed to maintain the whole system. 

All of above make clusters in-accessable to students and individual researchers. Usually, having access to a real cluster is desirable but not a must for many research programs. At the early stages of many research projects, we usually pilot our method on a small data set or a subset sampled from a big data set. The purpose is to have a priliminary sense of the data at hand and test if the methods could work.

In these cases, a large scale computing environment cannot be fully utlized. It would require a lot of overhead to get access to a cluster even before we can compute a mean for our data. Rather, we could use our controllable resources, i.e. personal computers, for emulating such a distributed computing environment. A good way to realize such an emulated environment is to build a local cluster consisting of virtual machines.

<font color='red'>... Some introduction to the background on virtual machines ...</font>

In this chapter, we demonstrate how to use [Oracle VM VirtualBox](https://www.virtualbox.org/) to build a virtual cluster. In the following example, we will build a cluster with three Ubuntu nodes. The operating system can be any linux distribution (or even windows). Though we only create three nodes, more nodes can be added if your personal computer is powerful enough. 

<font color='red'>... Some discussion on the pros and cons of different linux distributions, such as Redhat, CentOS, etc. </font>

## Installing One Virtual Machine (Node)


  
  

## Create more nodes and connect as a cluster