.. _mp:

===========
Marketplace
===========

Your OpenNebula installation is integrated with a few marketplaces. The most important one is the "`OpenNebula Public <https://marketplace.opennebula.io>`_" marketplace, which contains various appliances with base OS and even some popular services built and tested by the OpenNebula Systems.

Also, the images from `public LXD image server <https://us.images.linuxcontainers.org>`_ are available through the "Linux Containers" marketplace for the LXD environments. Please note these images are prepared by 3rd parties and all may not work seamlessly.

.. note::

    This section covers KVM and LXD evaluation environment.

    **For Firecracker**, you should use images from `DockerHub <https://hub.docker.com/>`_ as explained in advanced :ref:`Firecracker Deployment <firecracker-dockerhub>` section.

Check the enabled marketplaces in **Storage → MarketPlaces**:

|images-sunstone-marketplaces|

To see what appliances are available for you, go to **Storage → App**. Use the search input to filter the list on appliances in which you are interested. To import the appliance into your OpenNebula, select the required appliance and click on the cloud button.

|images-sunstone-apps|

Appliances usually come as a pair of virtual machine template and image. Both will be created in the OpenNebula. For the image, it's also necessary to select the storage location (datastore) where to import. Click on **Download** button to import the appliance.

|images-sunstone-apps-download|

To run the imported appliance, follow the same steps from section "Run Virtual Machine". Your new appliance will be available in the list. Please note the newly imported virtual machine templates don't come with any network configuration. You have to add a new network interface from (the only) available virtual network. For example:

|images-sunstone-apps-vm-create|

Continue with the official `MarketPlace <http://docs.opennebula.io/stable/advanced_components/marketplace>`_ documentation.


.. |images-sunstone-marketplaces| image:: /images/sunstone-marketplaces.png
.. |images-sunstone-apps| image:: /images/sunstone-apps.png
.. |images-sunstone-apps-download| image:: /images/sunstone-apps-download.png
.. |images-sunstone-apps-vm-create| image:: /images/sunstone-apps-vm-create.png
