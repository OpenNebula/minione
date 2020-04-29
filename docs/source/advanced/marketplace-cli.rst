.. _mp_cli:

====================
Marketplace over CLI
====================

Your OpenNebula comes with a few pre-configured marketplaces. They can be managed via ``onemarket`` command, e.g. listed, updated or deleted. Type following command to list configured Marketplaces:

.. prompt:: bash # auto

    # onemarket list
      ID NAME                                 SIZE AVAIL        APPS MAD     ZONE
       1 Linux Containers                       0M -              33 linuxco    0
       0 OpenNebula Public                      0M -              36 one        0

`Linux Containers <https://us.images.linuxcontainers.org/>`_ is an integration with public LXD image server (see the `documentation <http://docs.opennebula.io/stable/advanced_components/marketplace/market_lxd.html>`_). The `OpenNebula Public <https://marketplace.opennebula.io>`_ is the official public marketplace for the OpenNebula with appliances prepared and tested by the OpenNebula Systems. To list the appliances available in these marketplaces, use ``onemarketapp`` command:

.. prompt:: bash # auto

    # onemarketapp list

You can filter the output with standard stream processing tools, e.g. ``grep``:

.. prompt:: bash # auto

    # onemarketapp list | grep -i ubuntu
    68 ubuntu_xenial - LXD           1.0 1024M  rdy  img 05/27/19 Linux Containers   0
    67 ubuntu_trusty - LXD           1.0 1024M  rdy  img 05/27/19 Linux Containers   0
    66 ubuntu_eoan - LXD             1.0 1024M  rdy  img 05/27/19 Linux Containers   0
    65 ubuntu_disco - LXD            1.0 1024M  rdy  img 05/27/19 Linux Containers   0
    64 ubuntu_cosmic - LXD           1.0 1024M  rdy  img 05/27/19 Linux Containers   0
    63 ubuntu_bionic - LXD           1.0 1024M  rdy  img 05/27/19 Linux Containers   0
    62 ubuntu-core_16 - LXD          1.0 1024M  rdy  img 05/21/19 Linux Containers   0
    31 Ubuntu 16.04 with Docker  5.8.0-1  2.2G  rdy  img 02/26/19 OpenNebula Public  0
    29 Ubuntu 16.04 with Docker  5.8.0-1  2.2G  rdy  img 02/26/19 OpenNebula Public  0
    23 Ubuntu 14.04 - KVM        5.8.0-1  2.2G  rdy  img 02/26/19 OpenNebula Public  0
    20 Ubuntu for Docker Machine 0.6.0-2   10G  rdy  img 02/22/16 OpenNebula Public  0
    16 Ubuntu 18.10 - KVM        5.8.0-1  2.2G  rdy  img 02/26/19 OpenNebula Public  0
    15 Ubuntu 18.04 - KVM        5.8.0-1  2.2G  rdy  img 02/26/19 OpenNebula Public  0
    11 Ubuntu 16.04 - KVM        5.8.0-1  2.2G  rdy  img 02/26/19 OpenNebula Public  0
     8 Ubuntu 19.04 - KVM        5.8.0-1  2.2G  rdy  img 05/06/19 OpenNebula Public  0
     1 Ubuntu 18.04 - EC2        5.8.0-1    0M  rdy  tpl 02/26/19 OpenNebula Public  0
     0 Ubuntu 16.04 - EC2        5.8.0-1    0M  rdy  tpl 02/26/19 OpenNebula Public  0

These appliances can be used, but first need to be exported from the remote marketplace and imported into the selected own datastore. Datastore is a configured storage location in your OpenNebula installation, there are several types for different purposes. For this case, we need to know the *image datastore* for images. We use ``onedatastore`` command to list available datastores, e.g.:

.. prompt:: bash # auto

    # onedatastore list
      ID NAME                SIZE AVAIL CLUSTERS     IMAGES TYPE DS      TM      STAT
       2 files              71.4G 91%   0                 0 fil  fs      ssh     on
       1 default            71.4G 91%   0                 1 img  fs      qcow2   on
       0 system             71.4G 91%   0                 0 sys  -       qcow2   on

And, find the ID of only the image datastore (in default installation) with *img* in TYPE column. Based on the example outputs above, we'll use ``onemarketapp`` command to trigger the export of appliance 15 (Ubuntu 18.04 - KVM) into our image datastore 1 (default), and create a virtual machine template "Ubuntu 18.04" to quickly start the VM from this image. E.g.:

.. prompt:: bash # auto

    # onemarketapp export 15 'Ubuntu 18.04' -d 1
    IMAGE
        ID: 1
    VMTEMPLATE
        ID: 1

Show the available images and virtual machine templates to check that the appliance was imported with ``oneimage`` and ``onetemplate`` commands. The download of the image can take some time and to be able to use it, you have to wait until its status (STAT) switches to *rdy* state.

.. prompt:: bash # auto

    # onetemplate list
      ID USER            GROUP           NAME                                REGTIME
       1 oneadmin        oneadmin        Ubuntu 18.04                 05/27 18:13:08
       0 oneadmin        oneadmin        CentOS 7 - KVM               05/27 15:34:06

    # oneimage list
      ID USER       GROUP      NAME            DATASTORE     SIZE TYPE PER STAT RVMS
       1 oneadmin   oneadmin   Ubuntu 18.04    default       2.2G OS    No rdy     0
       0 oneadmin   oneadmin   CentOS 7 - KVM  default         8G OS    No rdy     0

The newly created template describes only a minimal virtual machine without networking. If we would run the virtual machine from the newly created template, the machine would run, but it wouldn't be possible to login over SSH. Virtual networks in the OpenNebula are always defined by the cloud administrators to fit one's own needs; there are no shared defaults. Your evaluation environment comes at least with a single virtual private network providing a masquerade to the virtual machines.

Show the available virtual networks:

.. prompt:: bash # auto

    # onevnet list
      ID USER            GROUP        NAME                CLUSTERS   BRIDGE   LEASES
       0 oneadmin        oneadmin     vnet                0          minioneb      0

If we want to run virtual machine from the imported appliance, we have to specify it should have a network interface card attached to selected network. E.g.,

.. prompt:: bash # auto

    # onetemplate instantiate 1 --nic 0
    VM ID: 1

Use ``onevm list`` and ``onevm show`` commands to find the IP address assigned to the virtual machine, and use ``ssh`` to login to it.
