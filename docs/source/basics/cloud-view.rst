.. _cloud_view:

==========
Cloud View
==========

The default Sunstone view above (admin or user) is powerful, but complex. It's suitable for the cloud administrators and advanced users. End-users might benefit from the "cloud view", which is a simplified Sunstone interface focused on the very basic virtual machine management operations.

To switch the view, click on the user name in the top right corner **Views → cloud**.

|images-sunstone-cloud-views|

The browser window should reload with a new layout. To run the virtual machine in the cloud view, click on the plus button **[+]** to start on the Dashboard or VMs tabs.

|images-sunstone-cloud-vm-add|

Select the prepared template, the name might differ from the one displayed on pictures based on selected evaluation environment type:

.. include:: ../shared/templates.txt

(Please note the initial template already has network interface preconfigured in the "Network" section below. If you later import additional appliances from the Marketplace or your own, you will need to assign the network interface to them).

Click on the **Create** button to start the virtual machine.

|images-sunstone-cloud-vm-create.png|

When we now go to the **VMs** tab, we can see our new machine. If the virtual machine is still not in the green running state, click the button with refresh icon to reload the data.

|images-sunstone-cloud-vm.png|

Click on the virtual machine to open the details with monitoring metrics and buttons to control the virtual machine state (e.g., open graphical console, make snapshot, terminate, power-off, or reboot).

|images-sunstone-cloud-vm-control|

Click on the "display" icon to open the graphical console. Login as user **root** with default password **opennebula** (can be changed in miniONE advanced deployment, see below). At the end, close the graphical console and click on the trash icon to termina the virtual machine.

Continue with the official `Cloud End-User <http://docs.opennebula.io/stable/operation/sunstone_enduser/>`_ documentation.

.. |images-sunstone-cloud-views| image:: /images/sunstone-cloud-views.png
.. |images-sunstone-cloud-vm-add| image:: /images/sunstone-cloud-vm-add.png
.. |images-sunstone-cloud-vm-create.png| image:: /images/sunstone-cloud-vm-create.png
.. |images-sunstone-cloud-vm.png| image:: /images/sunstone-cloud-vm.png
.. |images-sunstone-cloud-vm-control| image:: /images/sunstone-cloud-vm-control.png
