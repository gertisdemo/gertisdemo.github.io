---
---

* TOC
{:toc}

The Cluster Management component of <span>CLC</span> provides artefacts and tools for setting up and managing clusters. It utilizes the resources provided by the underlying OpenStack platform.

Cluster Management comprises a Cluster Management user interface (UI) and Cluster Provisioning.

### Cluster Management UI

CLC comes with a plugin for the OpenStack dashboard ([<u>Horizon</u>](http://docs.openstack.org/developer/horizon/)). It extends the dashboard with a panel the cluster operator can use for setting up and creating a new cluster by providing the following information:

*   **Name** of the cluster.

*   **Flavor**. Flavors are virtual hardware templates in OpenStack, defining sizes for RAM, disk, number of cores, and so on. The standard OpenStack installation provides several flavors. The default flavors are configurable by OpenStack administrators.
*   **Node count**. Number of nodes to be created in the cluster to be provisioned. Servers that perform work are called nodes. Node servers communicate with the master server, configure the networking for containers, and run the actual workloads assigned to them. An Atomic host image with the CentOS operating system is provided by <span>CLC</span> as base image for the nodes.

*   **Key pair for access & security**. Cloud images work with public key authentication rather than conventional user name/password authentication. When using the dashboard for the first time, a key pair must be created in OpenStack.

*   **IP pool**. Range of floating IP addresses that can be assigned to the nodes in the cluster to be provisioned.

In addition, the cluster operator can use the Cluster Management UI for terminating and deprovisioning a cluster.

For details, refer to the _Cluster Management Guide_.

### Cluster Provisioning

Cluster Provisioning is triggered via the Cluster Management UI when the cluster operator requests the creation of a cluster. Based on the input values, instructions for the provisioning of the cluster are created and passed to the OpenStack Orchestration (Heat) system.

<span>CLC</span> comes with predefined Heat orchestration templates (HOT). As part of the cluster setup, Heat is used to provision the VMs and configure the node operating system (CentOS). The preassembled base image for the nodes in the cluster is an [<u>Atomic</u>](http://www.projectatomic.io/) host. This is a node with a lean operating system designed to run Docker containers, built from upstream CentOS. It provides all the benefits of upstream distribution, plus the ability to perform Atomic upgrades and rollbacks.

Heat is responsible for the actual creation of the resources as well as the installation and configuration of Kubernetes (Cluster Orchestration) on top of them.
