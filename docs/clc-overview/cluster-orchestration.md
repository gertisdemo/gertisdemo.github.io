---
---

* TOC
{:toc}

Cluster Orchestration is the core of <span>CLC</span>. It utilizes [<u>Kubernetes</u>](http://kubernetes.io/), an open source project initiated by Google and developed by a large open source community. Below you find a description of the basic Kubernetes concepts.

### Master Server

The controlling unit in a Kubernetes cluster is called the master server. It serves as the main management contact point for administrators, and provides many cluster-wide services for the node servers.

The master server runs a number of unique services that are used to manage the cluster's workload and direct communication across the system.

### Node Server

In Kubernetes, servers that perform work are called nodes or node servers. Node servers communicate with the master server, configure the networking for containers, and run the actual workloads assigned to them.

Each individual node server is used to run [<u>Docker</u>](http://docs.docker.com/installation/windows/). The Docker service allows for running encapsulated application containers in a relatively isolated but lightweight operating environment. Each unit of work, at its basic level, is implemented as a series of containers that must be deployed.

In order to make services available to external parties, a proxy service runs on each node server. This service forwards requests to the correct containers, can do primitive load balancing, and is generally responsible for ensuring that the networking environment is predictable and accessible, but isolated.

### Kubernetes Workloads

While containers are used to deploy applications, the workloads that define each type of work are specific to Kubernetes. Kubernetes applies the following concepts:

*   **Clusters** are the compute resources on top of which the containers are build.
*   **Pods** are a collocated group of Docker containers with shared volumes. They are the smallest deployable units that can be created, scheduled, and managed by the Cluster Orchestration. Pods can be created individually, but the usage of replication controllers is recommended.
*   **Replication controllers** manage the lifecycle of pods. They ensure that a specific number of pods are running at a given time by creating or killing pods as required.
*   **Services** provide a single, stable name and address for a set of pods. They act as basic load balancers.
*   **Labels** are used to organize and select groups of objects based on key-value pairs.

### Kubernetes Interface

Interaction with Kubernetes is possible via a command line interface (CLI). The cluster user deploys and manages workloads on the cluster with it. The cluster operator uses it for maintenance and troubleshooting purposes, as well as for retrieving the status of a cluster and its resources. Via the CLI, the operator can also access the logical components of a cluster, such as services or replication controllers.
