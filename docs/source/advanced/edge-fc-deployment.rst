.. _edge-fc:

================================
Edge Deployment with Firecracker
================================

Similarly to Edge Deployment using KVM you can also use Firecracker. You simply add a ``--firecracker``
option to the command line.

When using Firecracker on Edge you can still pick the desired image from Docker Hub registry using the
``--fc-marketapp-name``.

+-------------------------------------------+--------------------------------------------------------+
| Parameter                                 | Description                                            |
+===========================================+========================================================+
| ``--fc-marketapp-name``                   | Dockerhub image for Firecracker                        |
+-------------------------------------------+--------------------------------------------------------+
| ``--fc-kernel-name``                      | Market app kernel name for Firecracker                 |
+-------------------------------------------+--------------------------------------------------------+

Examples
========

The basic Edge deployment on Packet with firecracker will be

.. prompt:: bash # auto

   # bash minione --firecracker --edge packet --edge-packet-token [<token>] --edge-packet-project [<project>]

