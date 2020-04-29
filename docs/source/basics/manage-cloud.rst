.. _manage:

============
Manage Cloud
============

The Sunstone web UI allows you to do all the cloud management operations. Walk through all the tabs available in the left panel to discover the entities which can be managed, and which are already preconfigured.

|images-sunstone-tabs|

Available tabs:

- **Instances.** Interface to manage existing virtual machines, services and virtual routers.

- **Templates.** Templates (configuration descriptors) of virtual machines, services, virtual routers and virtual machine groups. New instances are always created from the templates. *In default clean miniONE deployment, there should be imported a template for "CentOS 7".*

- **Storage.** Manage datastores (storage locations), and their content - images and files. Provides access to the marketplace. *By default clean miniONE deployment, 3 datastores are available - files, default (images), system. Datastores are configured to use space efficient QCOW2 driver. Default (image) datastore should contain base OS image with "CentOS 7".*

- **Network.** Manage virtual networks, templates, and security groups. Visualize network topology. *Default deployment comes with a virtual network "vnet". Virtual machines are provided with static private IP addresses, access to the public Internet service is via masquerade configured on the host.*

- **Infrastructure.** Manage virtualization infrastructure, hosts and clusters of hosts. Configure zones, several OpenNebula installations joined into a federation or highly-available service. *Default cluster with only a single local virtualization host (KVM, or LXD) is preconfigured.*

- **System.** Users, groups, and permissions (ACLs) management.

- **Settings.** Show and configure currently logged user.

.. |images-sunstone-tabs| image:: /images/sunstone-tabs.png
