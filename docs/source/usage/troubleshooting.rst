***************
Troubleshooting
***************

All OpenNebula services are running under unprivileged user **oneadmin**.

Logs are located in ``/var/log/one/``.

Main OpenNebula system services:

- ``opennebula.service`` - OpenNebula Cloud Controller Daemon
- ``opennebula-scheduler.service`` - OpenNebula Cloud Scheduler Daemon
- ``opennebula-sunstone.service`` - OpenNebula Sunstone Web UI Server
- ``opennebula-flow.service`` - OpenNebula Flow Server
- ``opennebula-gate.service`` - OpenNebula Gate Server
- ``opennebula-novnc.service`` - OpenNebula noVNC Server

Hypervisor services:

- ``libvirtd.service`` - Virtualization Daemon
- ``lxd.service`` - LXD Daemon

Use service management commands to control the service state.

Service Management
==================

Following examples describe the basic commands to control the system services:

.. code-block:: bash

    systemctl status opennebula.service

Stop service:

.. code-block:: bash

    systemctl stop opennebula.service

Start service:

.. code-block:: bash

    systemctl start opennebula.service

Disable service to start on boot:

.. code-block:: bash

    systemctl disable opennebula.service

Enable service to start on boot:

.. code-block:: bash

    systemctl enable opennebula.service

Futher Help
===========

Check and ask on `Community Forum <https://forum.opennebula.org/>`_.

Documentation:

- `OpenNebula Documentation <http://docs.opennebula.org/>`_
- `RHEL 7: Virtualization Deployment and Administration Guide <https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide>`_
- `LXD: Getting started - command-line <https://linuxcontainers.org/lxd/getting-started-cli/>`_
- `LXD: Documentation <https://lxd.readthedocs.io/en/latest/>`_

Found a bug or have an idea for a new feature? Check the existing issues and open a new one:

- general issues for `OpenNebula <https://github.com/OpenNebula/one/issues>`_
- only `miniONE <https://github.com/OpenNebula/minione/issues>`_ specific issues
