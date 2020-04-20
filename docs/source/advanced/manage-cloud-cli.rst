#####################
Manage Cloud over CLI
#####################

All cloud management operations (briefly described through the available Sunstone web UI tabs in the first part of this tutorial) can be done also via the set of powerful CLI tools. We'll again follow the Sunstone tabs to describe the group of commands, which provide the analogous functionality. All commands comes with rich manual page, which is displayed if command is run without any parameter.

|images-sunstone-tabs|

Commands covering following Sunstone tabs:

- **Instances**

  - ``onevm`` - manage virtual machines
  - ``oneflow`` - manage services
  - ``onevrouter`` - manage virtual routers

- **Templates**

  - ``onetemplate`` - manage virtual machine templates
  - ``oneflow-template`` - manage templates for services
  - ``onevmgroup`` - manage virtual machne groups

- **Storage**

  - ``onedatastore`` - manage datastores
  - ``oneimage`` - manage images and files
  - ``onemarket`` - manage configuration of marketplaces
  - ``onemarketapp`` - manage marketplace appliances

- **Network**

  - ``onevnet`` - manage virtual networks
  - ``onevntemplate`` - manage templates for virtual networks
  - ``onesecgroup`` - manage security groups

- **Infrastructure**

  - ``onecluster`` - manage clusters
  - ``onehost`` - manage virtualization hosts
  - ``onezone`` - manage federation and HA

- **System**

  - ``oneuser`` - manage users
  - ``onegroup`` - manage user groups
  - ``onevdc`` - manage virtual data centers
  - ``oneacl`` - manage ACLs

Most of the tools support ``list`` sub-command to show all available entities, and ``show`` to get detailed information about the particular one. Please try:

.. code-block:: bash

    # oneimage list
    # onetemplate list
    # onevm list
    # onehost list
    # onehost show localhost
    # onedatastore list
    # onevnet list
    # onevnet show 0
    # onecluster list
    # oneuser list
    # oneuser show oneadmin

Continue with the official `CLI Reference <http://docs.opennebula.org/stable/operation/references/cli.html>`_ and `Operation Guide <http://docs.opennebula.org/stable/operation/>`_.

.. |images-sunstone-tabs| image:: /images/sunstone-tabs.png
