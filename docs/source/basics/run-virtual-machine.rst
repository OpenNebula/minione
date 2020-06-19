.. _run_vm:

===================
Run Virtual Machine
===================

To run our first virtual machine, we stick with the easy-to-use Sunstone web UI.

In the left tab, click on **Instances → VMs** to get a (currently empty) list of running virtual machines. Click on the plus button **[+]** to start a new one.

|images-sunstone-vm-add|

Select the prepared template, the name might differ from the one displayed on pictures based on selected evaluation environment type:

.. include:: ../shared/templates.txt

(Please note the initial template already has network interface preconfigured in the "Network" section below. If you later import additional appliances from the Marketplace or your own, you will need to assign the network interface to them.)

Click on the **Create** button to start the virtual machine.

|images-sunstone-vm-create|

When we go back to the list of virtual machines in **Instances → VMs**, we can see our new machine. If the virtual machine is still not in RUNNING, click the button with refresh icon to reload the data.

|images-sunstone-vm-control|

When the virtual machine is running, the "display" icon allows to open a graphical console. Login as user **root** with default password **opennebula** (can be changed in miniONE advanced deployment, see below).

You can validate the virtual machine can reach the public internet services. E.g.:

|images-sunstone-vm-vnc|

While being logged on your frontend under **root** or **oneadmin** user, you can login your virtual machine over SSH. The IP address of the virtual machine is visible in the virtual machines list.

.. prompt:: bash # auto

    # ssh root@172.16.100.2
    Warning: Permanently added '172.16.100.2' (ECDSA) to the list of known hosts.
    Last login: Mon May 20 14:16:55 2019 from 172.16.100.1
    [root@localhost ~]#

.. note::

    Remember that in local all-in-one deployments (with KVM/LXD/Firecracker) the VMs still have only private IP addresses. By default from the range ``172.16.100.0/24``. So the first VM will get ``172.16.100.2`` as the ``.1`` is used for the miniONE frontend.

    If you want to reach the private VM from the outside by sharing the IP address of the miniONE host, you can **forward** communication over the selected host port to the particular port of private VM. For example, the following command ensures that miniONE host port 8080 is forwarded to port 80 of the VM with IP address ``172.16.100.2``:

    .. prompt:: bash # auto

        # iptables -t nat -I PREROUTING -p tcp --dport 8080 -j DNAT --to 172.16.100.2:80

    (i.e., if you point your browser to your miniONE host and port 8080, e.g. ``http://minione:8080``, it reaches the port 80 of your private VM).

To terminate the virtual machine, go back to the Sunstone web UI to **Instances → VMs**. Select the particular virtual machine and click on the trash button to terminate it.

|images-sunstone-vm-terminate|

Continue with the official `Virtual Machine Management <http://docs.opennebula.io/stable/operation/vm_management/>`_ documentation.

.. |images-sunstone-vm-add| image:: /images/sunstone-vm-add.png
.. |images-sunstone-vm-create| image:: /images/sunstone-vm-create.png
.. |images-sunstone-vm-control| image:: /images/sunstone-vm-control.png
.. |images-sunstone-vm-vnc| image:: /images/sunstone-vm-vnc.png
.. |images-sunstone-vm-terminate| image:: /images/sunstone-vm-terminate.png
