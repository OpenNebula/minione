.. _advanced_vm:

============================
Run Virtual Machine over CLI
============================

In the sections above, we have covered how to run your first virtual machine over the Sunstone web interface. The following sections focus more on using and managing OpenNebula over the command line interface. It's expected that all the commands are executed on the evaluation front-end under privileged user **root** or **oneadmin**.

Firstly, we list available templates from which the virtual machines can be created:

.. prompt:: bash # auto

    # onetemplate list
      ID USER            GROUP           NAME                                REGTIME
       0 oneadmin        oneadmin        CentOS 7 - KVM               04/12 13:38:39

We run the virtual machine with template ID found in the list passed to the following command:

.. prompt:: bash # auto

    # onetemplate instantiate 0
    VM ID: 5

After the virtual machine is instantiated, the command returns its unique ID. We'll use this identifier in other commands when referencing to the virtual machine.

Check the virtual machine state, wait until it's running:

.. prompt:: bash # auto

    # onevm list
        ID USER     GROUP    NAME            STAT UCPU    UMEM HOST             TIME
         5 oneadmin oneadmin CentOS 7 - KVM- runn    0      0K localhost    0d 00h00

We can now login to the virtual machine, but first we need to know which IP address was assigned to the instance. Let's query the virtual machine metadata with the following command and find the required IP address in section with "VM NICS":

.. prompt:: bash # auto

    # onevm show 5
    VIRTUAL MACHINE 5 INFORMATION                                                   
    ID                  : 5                   
    NAME                : CentOS 7 - KVM-5    
    USER                : oneadmin            
    GROUP               : oneadmin            
    STATE               : ACTIVE              
    LCM_STATE           : RUNNING             
    ...

    VM NICS                                                                         
     ID NETWORK              BRIDGE       IP              MAC               PCI_ID
      0 vnet                 minionebr    172.16.100.2    02:00:ac:10:64:02

Finally, we can login into the virtual machine:

.. prompt:: bash # auto

    # ssh root@172.16.100.2
    Warning: Permanently added '172.16.100.2' (ECDSA) to the list of known hosts.
    Last login: Fri Apr 12 14:31:36 2019 from 172.16.100.1
    [root@localhost ~]#

To shutdown the virtual machine, return back to the front-end host and type:

.. prompt:: bash # auto

    # onevm terminate 5

Check again the list of virtual machines to watch how the virtual machine is switching between shutdown and epilog phases, and finally disappearing from the list:

.. prompt:: bash # auto

    # onevm list
        ID USER     GROUP    NAME            STAT UCPU    UMEM HOST             TIME
