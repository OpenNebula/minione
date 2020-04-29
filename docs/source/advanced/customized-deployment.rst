.. _advanced_deploy:

=====================
Customized Deployment
=====================

The default deployment doesn't have to fit everyone, or even the required resources (bridge, IP range, port) can be already used by other services. To deal with these cases, the miniONE tool has several command line switches, which can adjust the deployment and configuration of particular parts.

This section covers advanced parameters for local KVM and LXD evaluation environments. See more options specific to **edge deployment** in section :ref:`Edge Deployment <edge>`.

The most common command line switches (followed by their defaults):

+---------------------------------------+------------------------------------------------------+
| Parameter                             | Description                                          |
+=======================================+======================================================+
| ``--help``                            | Show all available command line switches.            |
+---------------------------------------+------------------------------------------------------+
| ``--verbose``                         | Verbose logging.                                     |
+---------------------------------------+------------------------------------------------------+
| ``--lxd``                             | Deploy environment to evaluate LXD hypervisor.       |
+---------------------------------------+------------------------------------------------------+
| ``--version`` X.Y                     | Specify particular OpenNebula version to deploy      |
+---------------------------------------+------------------------------------------------------+
| ``--frontend``                        | Frontend only. Skip hypervisor / net. configuration. |
+---------------------------------------+------------------------------------------------------+
| ``--sunstone-port`` 80                | Port to bind the Sunstone web UI                     |
+---------------------------------------+------------------------------------------------------+
| ``--password`` RANDOM                 | Initial password for dedicated oneadmin user         |
+---------------------------------------+------------------------------------------------------+
| ``--vm-password`` opennebula          | Password to login VMs over integrated VNC            |
+---------------------------------------+------------------------------------------------------+
| ``--purge``                           | Uninstall OpenNebula and remove all traces.          |
+---------------------------------------+------------------------------------------------------+

The host operating system is reconfigured to be able to run virtual machines on one's own dedicated network bridge with a non-clashing IP range. The OpenNebula internals are prepared to run your first virtual machine in just a single click. Additional host firewall configuration enables the IP Masquerade (NAT) to allow the virt. machines access to the public Internet services.

Note: Virtual machines are provided only with private IP addresses. They can communicate with the public Internet services, but they "hide" behind the IP address of your dedicated host. While you can connect the public services from virtual machines, the virtual machines are not reachable from outside the dedicated host.

Simplified host configuration after deployment:

|images-host-networking|

Following parameters can specify the existing NIC for masquerade, choose name of the private network bridge to create, and customize the IP configuration of the virtual private networking:

+-------------------------------------+------------------------------------------+
| Parameter                           | Description                              |
+=====================================+==========================================+
| ``--nat-interface`` [autodetected]  | Name of existing main NIC for masquerade |
+-------------------------------------+------------------------------------------+
| ``--bridge-interface`` minionebr    | Bridge interface for private networking  |
+-------------------------------------+------------------------------------------+
| ``--vnet-address`` 172.16.100.0     | Virtual Network address                  |
+-------------------------------------+------------------------------------------+
| ``--vnet-netmask`` 255.255.255.0    | Virtual Network netmask                  |
+-------------------------------------+------------------------------------------+
| ``--vnet-gateway`` 172.16.100.1     | Virtual Network gateway (i.e. bridge IP) |
+-------------------------------------+------------------------------------------+
| ``--vnet-ar-ip-start`` 172.16.100.1 | Virtual Network address range start IP   |
+-------------------------------------+------------------------------------------+
| ``--vnet-ar-ip-count`` 100          | Virtual Network address range size       |
+-------------------------------------+------------------------------------------+

Into the fresh deployment, the base OS image with CentOS 7 is imported from the public `OpenNebula Marketplace <https://marketplace.opennebula.io/>`_. This image can be easily instantiated with a single click. Different OS images can be specified, but the name must precisely match the unique name on the Marketplace via option:

+--------------------------------------------+---------------------------+
| Parameter                                  | Description               |
+--------------------------------------------+---------------------------+
| ``--marketapp-name`` 'CentOS 7 - KVM'      | Appliance name            |
+--------------------------------------------+---------------------------+

We have to choose the favourite appliance on the Marketplace web, open the appliance details and find the full unique name in the title. E.g., for the Ubuntu 18.04, find the full name 'Ubuntu 18.04 - KVM'.

|images-marketplace-app|

Examples
========

Verbose deployment of LXD environment

.. prompt:: bash # auto

    # bash minione --verbose --lxd

Verbose deployment of KVM environment, custom password for OpenNebula user:

.. prompt:: bash # auto

    # bash minione --verbose --password MySecretPassword

Set NAT interface and custom bridge name:

.. prompt:: bash # auto

    # bash minione --nat-interface eth1 --bridge-interface privbr0

Custom private network IP range for virtual networking:

.. prompt:: bash # auto

    # bash minione --vnet-address 192.0.2.0 --vnet-gateway 192.0.2.1 --vnet-ar-ip-start 192.0.2.2

Import Alpine Linux VM image (instead of default CentOS) and run Sunstone web UI on port 8080:

.. prompt:: bash # auto

    # bash minione --marketapp-name 'Alpine Linux 3.8 - KVM' --sunstone-port 8080

.. |images-host-networking| image:: /images/host-networking.png
.. |images-marketplace-app| image:: /images/marketplace-app.png
