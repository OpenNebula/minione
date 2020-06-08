.. _whats:

========
What is?
========

OpenNebula is a lightweight datacenter management solution to operate the private, public, and hybrid clouds running on the KVM, LXD, and VMware technologies. It can serve small compact clouds with just a few nodes, and scale to thousands of computing cores over multiple federated zones. It's easy to install, maintain and upgrade, and comes with its own `Marketplace <https://marketplace.opennebula.io>`_, offering a selection of base appliances with popular Linux distributions with which you can quickly start. Extensive `documentation <http://docs.opennebula.io>`_ covers wide range of uses, from the individual end-user to the cloud administrator preparing the deployment.

In this guide, we'll go through the special type of deployment, the all-in-one OpenNebula environment. All the necessary services to use, manage and run the cloud will be colocated on the single dedicated bare-metal host.

While all the installation and configuration steps could be done manually by following the official documentation and would give you a better insight and control over what and how it is configured, we'll focus on the most straightforward approach leveraging the miniONE tool.

The `miniONE <https://github.com/OpenNebula/minione>`_ tool is simple deployment script which prepares the all-in-one OpenNebula environments. Such deployments are mainly intended for evaluation, development and testing, but can also be used as a base for larger short-lived deployments. Usually, it takes just a few minutes to get the environment ready. The tool can prepare evaluation environments for true virtual machines running on KVM hypervisors, or the system containers running on LXD hypervisors. Another option which we call *Edge deployment* includes OpenNebula frontend and configured KVM hypervisors on public Cloud providers. And lastly, you can have environment prepared for running micro VMs on Firecracker hypervisor.
