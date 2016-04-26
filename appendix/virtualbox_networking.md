# VirtualBox Networking[^ref_source]

VirtualBox provides up to eight virtual PCI Ethernet cards for each virtual machine. For each such card, you can individually select (1) the hardware that will be virtualized as well as (2) the virtualization mode that the virtual card will be operating in with respect to your physical networking hardware on the host.

Four of the network cards can be configured in the "Network" section of the settings dialog in the VirtualBox GUI. You can configure all eight network cards on the command line via VBoxManage ｀modifyvm｀。

## 1. Virtual Networking Hardware

For each card, you can individually select what kind of hardware will be presented to the virtual machine. VirtualBox can virtualize the following six types of networking hardware:

1. AMD PCNet PCI II (Am79C970A);
2. AMD PCNet FAST III (Am79C973, the default);
3. Intel PRO/1000 MT Desktop (82540EM);
4. Intel PRO/1000 T Server (82543GC);
5. Intel PRO/1000 MT Server (82545EM);
6. Paravirtualized network adapter (virtio-net).

The PCNet FAST III is the default because it is supported by nearly all operating systems out of the box, as well as the GNU GRUB boot manager. As an exception, the Intel PRO/1000 family adapters are chosen for some guest operating system types that no longer ship with drivers for the PCNet card, such as Windows Vista. More details about hardware can be found on [VirtualBox's networking manual page](https://www.virtualbox.org/manual/ch06.html).


## 2. Introduction to Networking Modes

Each of the eight networking adapters can be separately configured to operate in one of the following modes:

1. **Not attached** In this mode, VirtualBox reports to the guest that a network card is present, but that there is no connection -- as if no Ethernet cable was plugged into the card. This way it is possible to "pull" the virtual Ethernet cable and disrupt the connection, which can be useful to inform a guest operating system that no network connection is available and enforce a reconfiguration.

2. **Network Address Translation (NAT)** If all you want is to browse the Web, download files and view e-mail inside the guest, then this default mode should be sufficient for you.

3. **NAT Network** The NAT network is a new NAT flavour introduced in VirtualBox 4.3.

4. **Bridged networking** This is for more advanced networking needs such as network simulations and **running servers in a guest**. When enabled, VirtualBox connects to one of your installed network cards and exchanges network packets directly, circumventing your host operating system's network stack.

5. **Internal networking** This can be used to create a different kind of software-based network which is visible to selected virtual machines, but not to applications running on the host or to the outside world. <font color='red'>One use case is that it can be used for connecting the back end nodes in a cluster.</font>

6. **Host-only networking** This can be used to create a network containing the host and a set of virtual machines, without the need for the host's physical network interface. Instead, a virtual network interface (similar to a loopback interface) is created on the host, providing connectivity among virtual machines and the host.

7. **Generic networking** 

---

[^ref_source]: This article is copied from [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html).