.. _edge:

===============
Edge Deployment
===============

When running the Edge deployment, most of the parameters are related to the remote cloud provider - `Packet <https://packet.net>`_. For the details consult `Packet API documentation <https://www.packet.com/developers/api>`_. If there are commands `curl` and `jq` available on the system the parameters will be validated before the installation starts.

+-------------------------------------------+--------------------------------------------------------+
| Parameter                                 | Description                                            |
+===========================================+========================================================+
| ``--edge`` packet                         | Edge provider                                          |
+-------------------------------------------+--------------------------------------------------------+
| ``--edge-packet-token`` [token]           | Packet token (required with ``--edge packet``)         |
+-------------------------------------------+--------------------------------------------------------+
| ``--edge-packet-project`` [project]       | Packet project (required with ``--edge packet``)       |
+-------------------------------------------+--------------------------------------------------------+
| ``--edge-host-num`` 1                     | Number of edge hosts                                   |
+-------------------------------------------+--------------------------------------------------------+
| ``--edge-packet-facility`` ams1           | Packet facility                                        |
+-------------------------------------------+--------------------------------------------------------+
| ``--edge-packet-plan`` t1.small           | Packet plan                                            |
+-------------------------------------------+--------------------------------------------------------+
| ``--edge-packet-os`` ubuntu_18_04         | Packet OS                                              |
+-------------------------------------------+--------------------------------------------------------+

Appliance
=========

By default miniONE will prepare ``Service WordPress`` but you can choose what applicance you like from the `Market Place <https://marketplace.opennebula.io/appliance>`_.

+---------------------------------------------------------+-----------------------------------------+
| Parameter                                               | Description                             |
+=========================================================+=========================================+
| ``--edge-marketapp-name`` 'Service WordPress - KVM'     | Market app name for Packet              |
+---------------------------------------------------------+-----------------------------------------+

Frontend or Node
================

The edge deployment might be started with the ``--frontend`` paramter then only the frontend setup will be done. Later, you can run ``minione`` again (even multiple times) with the ``--node`` which will provision new node in the cloud.

+------------------+--------------------------------------------------------+
| Parameter        | Description                                            |
+==================+========================================================+
| ``--frontend``   | Install only frontend, skip node setup                 |
+------------------+--------------------------------------------------------+
| ``--node``       | Install only node                                      |
+------------------+--------------------------------------------------------+

Examples
========

The simpliest Edge deployment on Packet will be

.. prompt:: bash # auto

   # bash minione --edge packet --edge-packet-token [<token>] --edge-packet-project [<project>]

Adding additional Edge node to existing installation

.. prompt:: bash # auto

   # bash minione --edge packet --node --edge-packet-token [<token>] --edge-packet-project [<project>]

To install just the frontend but don't provision any Edge node yet

.. prompt:: bash # auto

   # bash minione --edge packet --frontend --edge-packet-token [<token>] --edge-packet-project [<project>]
