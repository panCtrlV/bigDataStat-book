# VirtualBox Networking[^ref_source]

VirtualBox provides up to eight virtual PCI Ethernet cards for each virtual machine. For each such card, you can individually select (1) the hardware that will be virtualized as well as (2) the virtualization mode that the virtual card will be operating in with respect to your physical networking hardware on the host.

Four of the network cards can be configured in the "Network" section of the settings dialog in the VirtualBox GUI. You can configure all eight network cards on the command line via VBoxManage ｀modifyvm｀。

For each card, you can individually select what kind of hardware will be presented to the virtual machine. VirtualBox can virtualize the following six types of networking hardware:

1. AMD PCNet PCI II (Am79C970A);
2. AMD PCNet FAST III (Am79C973, the default);
3. Intel PRO/1000 MT Desktop (82540EM);
4. Intel PRO/1000 T Server (82543GC);
5. Intel PRO/1000 MT Server (82545EM);
6. Paravirtualized network adapter (virtio-net).

---

[^ref_source]: This article is copied from [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html).