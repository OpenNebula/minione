.. _firecracker:

===========
Firecracker
===========

OpenNebula 5.12 introduces support for running micro VMs via **Firecracker** hypervisor.

Similarly as with KVM or LXD, for the Firecracker you need to pass ``--firecracker`` option. As before, miniONE prepares
an image for you, specify the image from the Dockerhub registry using the ``--fc-marketapp-name`` option, by default it's
the latest ``alpine`` image.  Also Firecracker requires special kernel you can specify its name using ``--fc-kernel-name``
(option usually you don't need to modify these values).

+----------------------------------------------------------+------------------------------------------------------------------+
| Parameter                                                | Description                                                      |
+==========================================================+==================================================================+
| ``--firecracker``                                        | Show all available command line switches.                        |
+----------------------------------------------------------+------------------------------------------------------------------+
| ``--fc-marketapp-name`` 'alpine'                         | Dockerhub image for Firecracker                                  |
+----------------------------------------------------------+------------------------------------------------------------------+
| ``--fc-kernel-name`` 'Kernel 5.4 x86_64 - Firecracker'   | Market app kernel name for Firecracker.                          |
+----------------------------------------------------------+------------------------------------------------------------------+

The rest of the parameters, especially the networking, remains the same as for the KVM orLXD. The integration is seemless.

Examples
========

Verbose deployment of Firecracker environment

.. prompt:: bash # auto

    # bash minione --verbose --firecracker

Verbose deployment of Firecracker, import latest ``ubuntu`` image.

.. prompt:: bash # auto

    # bash minione --verbose --firecracker --fc-marketapp-name ubuntu


.. _firecracker-dockerhub:

======================================
Image from DockerHub and Kernel update
======================================

Trying different image with Firecracker is a little bit different from KVM and LXD because Firecracker
micro VMs require specific Kernel to be used. This Kernel is available on OpenNebula Public Marketplace
and miniONE downloads it always during the installation. What remains is to link the Kernel from the VM
template as we show in the following example.

First, go to **Storage** -> **Apps** tab and pick an Image from the DockerHub, e.g. **nginx** like here

|images-sunstone-dockerhub|

Download the image to the only image datastore we have

|images-sunstone-dockerhub-import-nginx|

Now we need to update the VM template, navigate to the **Templates** -> **VMs** -> **nginx** and switch to **Template**
tab.

|images-sunstone-update-template|

Click the **Update** button and switch to **Advanced** mode. Update the **OS** section with this snippet


.. code::

    OS = [
      KERNEL_CMD = "console=ttyS0 reboot=k panic=1 pci=off i8042.noaux i8042.nomux i8042.nopnp i8042.dumbkbd",
      KERNEL_DS = "$FILE[IMAGE=\"kernel\"]" ]

|images-sunstone-update-template-replace-kernel|

After you save the template and wait until the image is fully downloaded it is ready to start the micro VM.

.. |images-sunstone-dockerhub| image:: /images/sunstone-dockerhub.png
.. |images-sunstone-dockerhub-import-nginx| image:: /images/sunstone-dockerhub-import-nginx.png
.. |images-sunstone-update-template| image:: /images/sunstone-update-template.png
.. |images-sunstone-update-template-replace-kernel| image:: /images/sunstone-update-template-replace-kernel.png
