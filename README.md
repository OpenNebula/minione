# miniONE

**miniONE** is an easy to use deployment tool to build an evaluation OpenNebula cloud based on virtual machines (KVM). All necessary components to manage and run the virtual machines are installed and configured on your dedicated system with just a single command run.

**Follow the detailed [tutorial](https://docs.opennebula.io/stable/quick_start/deployment_basics/overview.html)**.

## Requirements
You’ll need a server (physical or virtual) to try out OpenNebula. The provided Host should have a fresh default installation of the required operating system with the latest updates and without any customizations.

- 4 GiB RAM
- 20 GiB free space on disk
- privileged user access (root)
- openssh-server package installed
- operating system: RHEL/AlmaLinux 8 or 9, Debian 10 or 11, Ubuntu 18.04, 20.04 or 22.04
- open ports: 22 (SSH), 80 (Sunstone), 2616 (FireEdge)

## Quickstart

Download the [latest release](https://github.com/OpenNebula/minione/releases/latest) of the **miniONE** tool, run it and follow the instructions on the terminal.

### Get Frontend Only

Run the following commands to deploy only the OpenNebula frontend:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione --frontend
```

For frontend only installation either a virtual machine or bare-metal host could be used. Afterwards, you can  follow this [tutorial](https://docs.opennebula.io/stable/quick_start/deployment_basics/overview.html) to deploy edge clusters on-premises or on-cloud.

### Get Frontend and KVM Node Cloud

Run the following commands to deploy an evaluation cloud with a front-end and a single KVM node:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione
```

This option is suitable for bare-metal hosts to utilize HW virtualization, however the deployment will fallback to emulation (QEMU) if running on virtual machine or CPU without the virt. capabilities.

## License

Copyright 2002-2023, OpenNebula Systems (formerly C12G Labs)

Licensed under the Apache License, Version 2.0 (the "License"); you may
not use this file except in compliance with the License. You may obtain
a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
