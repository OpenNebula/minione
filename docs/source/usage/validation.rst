**********
Validation
**********

Check that the base installation is working correctly by listing the hypervisor hosts.

.. code-block:: bash

    # onehost list
      ID NAME            CLUSTER   TVM      ALLOCATED_CPU      ALLOCATED_MEM STAT
       0 localhost       default     0       0 / 400 (0%)     0K / 7.8G (0%) on


You should find your dedicated node configured as a hypervisor "localhost" in the **on** state (STAT).

Or, point your browser to the Sunstone web URL provided in the deployment report above, and login the user **oneadmin** with provided credentials.

|images-sunstone-dashboard|

If the host configured by **miniONE** is behind the firewall, the (default) Sunstone port 80 has to be enabled for the machine you are connecting from.

.. |images-sunstone-dashboard| image:: /images/sunstone-dashboard.png

