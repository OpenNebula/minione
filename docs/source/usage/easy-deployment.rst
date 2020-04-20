***************
Easy deployment
***************

Various command line parameters passed to the miniONE tool can customize the deployment process, e.g. required OpenNebula version or initial passwords. You can get a list of available switches by running:

.. code-block:: bash

    bash minione --help

In most cases, it's not necessary to specify anything and simply proceed with installation.

If needed, the deployment customization is covered by next section "Advanced Installation".

You have to choose between the KVM (default), LXD or Edge evaluation environment. Run the following command under the privileged user **root** to get ready the all-in-one OpenNebula installation with default KVM hypervisor:

.. code-block:: bash

    bash minione


Or, for LXD environment:

.. code-block:: bash

    bash minione --lxd


Or, for Edge environment on Packet:

.. code-block:: bash

    bash minione --edge packet --edge-packet-token [token] --edge-packet-project [project]


Be patient, it should take only a few minutes to get the host prepared. Main deployment steps are logged on the terminal and at the end of a successful deployment, the miniONE tool provides a report with connection parameters and initial credentials. For example:

.. code-block:: bash

    ### Report
    OpenNebula 5.8 was installed
    Sunstone (the webui) is running on:
      http://192.0.2.1/
    Use following to login:
      user: oneadmin
      password: t5mk2tvPCG

When running the Edge deployment you will see also similar report:

.. code-block:: bash

    ### Packet provisioned
      ID NAME            CLUSTER   TVM      ALLOCATED_CPU      ALLOCATED_MEM STAT
       0 147.75.84.183   PacketClu   0                  -                  - init

To extend the setup by additional hypervisor on Packet run following command:

.. code-block:: bash

    ./minione --edge packet --node --edge-packet-token [<token>] --edge-packet-project [<project>]


To cleanup (delete resources in OpenNebula and Packet) run:


.. code-block:: bash

    oneprovision delete aeb1e3e0-09fd-426c-9ee5-13ee60daeee7 --cleanup


Now, the all-in-one OpenNebula evaluation environment is ready.

The rest of the guide introduces "how to run the very first virtual machine in a single click", "how to control the virtual machine state" and "how to explore the infrastructure defined in the OpenNebula" - first, utilizing the Sunstone web UI, and later using CLI as part of the Advanced sections. If you are familiar with the OpenNebula, you can skip the rest.
