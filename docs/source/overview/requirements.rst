.. _requirements:

============
Requirements
============

Requirements may differ for various types of evaluation environments which you may deploy. In all cases, the provided host should have a fresh default installation of required operating system with latest updates and without any customizations.

Common minimal requirements
===========================
- 4 GiB RAM
- 20 GiB free space on disk
- default installation of the operating system with the latest updates
- privileged user access (`root`)
- openssh-server package installed

Virtual Machines (KVM)
======================
|images-minione-kvm.png|

For KVM evaluation on a dedicated physical server for the front-end and one KVM hypervisor node the minimal requirements are:

* x86-64 Intel or AMD processor with **virt. capabilities**
* physical host or virtual machine supporting the nested virtualization
* operating system: CentOS 7 or 8, Debian 9 or 10, Ubuntu 16.04, 18.04 or 20.04


System Containers (LXD)
=======================
|images-minione-lxd|

For LXD evaluation on a dedicated physical server or virtual machine for the front-end and one LXD hypervisor node the minimal requirements are:

* x86-64 Intel or AMD processor
* physical host or virtual machine
* operating system: Ubuntu 18.04 or 20.04

Firecracker Micro VMs
=======================
|images-minione-firecracker|

For Firecracker evaluation on a dedicated physical server or virtual machine for the front-end and one Firecracker hypervisor node the minimal requirements are:

* x86-64 Intel or AMD processor
* physical host or virtual machine
* operating system: CentOS 7 or 8, Debian 9 or 10, Ubuntu 16.04, 18.04 or 20.04

Edge deployment + KVM on Packet
===============================
|images-minione-packet|

For Edge evaluation on a dedicated physical server or virtual machine for the front-end and one remote Packet edge physical server for one KVM hypervisor node the minimal requirements are

for the frontend

* x86-64 Intel or AMD processor
* physical host or virtual machine
* operating system: CentOS 7, Debian 9, Ubuntu 16.04 or 18.04

for the hypervisor(s) on Packet

* Packet API token
* Packet API project

The deployment process with the `miniONE <https://github.com/OpenNebula/minione>`_ tool is so quick and easy, that you can switch to the new machine at any time your existing one doesn't fit anymore.

.. |images-minione-kvm.png| image:: /images/minione-kvm.png
.. |images-minione-lxd| image:: /images/minione-lxd.png
.. |images-minione-firecracker| image:: /images/minione-firecracker.png
.. |images-minione-packet| image:: /images/minione-packet.png
