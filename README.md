# miniONE

**miniONE** is an easy to use deployment tool to build an evaluation OpenNebula cloud based on virtual machines (KVM). All necessary components to manage and run the virtual machines are installed and configured on your dedicated system with just a single command run.

**Follow the detailed [tutorial](http://docs.opennebula.io/6.0/quick_start/deployment_basics/try_opennebula_on_kvm.html)**.

## Requirements
You’ll need a server (physical or virtual) to try out OpenNebula. The provided Host should have a fresh default installation of the required operating system with the latest updates and without any customizations.

- 4 GiB RAM
- 20 GiB free space on disk
- privileged user access (root)
- openssh-server package installed
- operating system: CentOS 7 or 8, Debian 9 or 10, Ubuntu 18.04 or 20.04
- open ports: 22 (SSH), 80 (Sunstone), 2616 (FireEdge)


## Quickstart

Download the [latest release](https://github.com/OpenNebula/minione/releases/latest) of the **miniONE** tool, run it and follow the instructions on the terminal.

### Get Frontend Only

Run the commands to deploy only the OpenNebula frontend:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione --frontend
```

For frontend only installation either virtual machine or bare-metal host could be used.

### Get Frontend and KVM Node Cloud

Run the commands to deploy an evaluation cloud with a front-end and a single KVM node:

```
wget 'https://github.com/OpenNebula/minione/releases/latest/download/minione'
sudo bash minione
```

This option is suitable for bare-metal hosts to utilize HW virtualization, however the deployment will fallback to emulation (QEMU) if running on virtual machine or CPU without the virt. capabilities.

## License

Copyright 2002-2021, OpenNebula Project, OpenNebula Systems (formerly C12G Labs)

Licensed under the Apache License, Version 2.0 (the "License"); you may
not use this file except in compliance with the License. You may obtain
a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
