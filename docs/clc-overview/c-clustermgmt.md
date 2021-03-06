---
---

<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xml:lang="en-us" lang="en-us">
<head>
<meta content="text/html; charset=utf-8" http-equiv="Content-Type" />
<meta name="copyright" content="(C) Copyright 2005" />
<meta name="DC.rights.owner" content="(C) Copyright 2005" />
<meta content="concept" name="DC.Type" />
<meta name="DC.Title" content="Cluster Management" />
<meta name="prodname" content="ServerView" />
<meta content="1.1" name="version" />
<meta name="brand" content="FUJITSU Software" />
<meta name="component" content="" />
<meta name="prognum" content="Cloud Load Control V1.1" />
<meta name="series" content="Overview" />
<meta content="XHTML" name="DC.Format" />
<meta content="ClusterMgmt" name="DC.Identifier" />
<meta content="en-us" name="DC.Language" />
<link href="../../commonltr.css" type="text/css" rel="stylesheet" />
<link href="../../book.css" type="text/css" rel="stylesheet" />
<title>Cluster Management</title>
</head>
<body id="ClusterMgmt">


    <h1 class="topictitle1">Cluster Management</h1>

    <div>
        <div class="section">
            <p>The Cluster Management component of <span>CLC</span> provides artefacts and tools for setting up and managing clusters. It utilizes the resources provided by the underlying OpenStack platform. </p>

            <p>Cluster Management comprises a Cluster Management user interface (UI) and Cluster Provisioning. </p>

        </div>

        <div class="section"><h4 class="sectiontitle">Cluster Management UI</h4>

            <p><span>CLC</span> comes with a plugin for the OpenStack dashboard (<a href="http://docs.openstack.org/developer/horizon/" target="_blank"><u>Horizon</u></a>). It extends the dashboard with a panel the cluster operator can use for setting up and creating a new cluster by providing the following information:</p>

            <div class="p">
                <ul>
                    <li><strong>Name</strong> of the cluster.</li>

                    <li><strong>Flavor</strong>. Flavors are virtual hardware templates in OpenStack, defining sizes for RAM, disk, number of cores, and so on. The standard OpenStack installation provides several flavors. The default flavors are configurable by OpenStack administrators. </li>

                    <li><strong><strong>Node count</strong></strong>. Number of nodes to be created in the cluster to be provisioned. Servers that perform work are called nodes. Node servers communicate with the master server, configure the networking for containers, and run the actual workloads assigned to them. An Atomic host image with the CentOS operating system is provided by <span>CLC</span> as base image for the nodes. </li>


                    <li><strong>Key pair for access &amp; security</strong>
                        <p>Cloud images work with public key authentication rather than conventional user name/password authentication. When using the dashboard for the first time, a key pair must be created in OpenStack.</p>
</li>

                    <li><strong>IP pool</strong>. Range of floating IP addresses that can be assigned to the nodes in the cluster to be provisioned.</li>

                </ul>

            </div>

            <p>In addition, the cluster operator can use the Cluster Management UI for terminating and deprovisioning a cluster. </p>

            <p>For details, refer to the <em>Cluster Management Guide</em>. </p>

        </div>

        <div class="section"><h4 class="sectiontitle">Cluster Provisioning</h4>

            <p>Cluster Provisioning is triggered via the Cluster Management UI when the cluster operator requests the creation of a cluster. Based on the input values, instructions for the provisioning of the cluster are created and passed to the OpenStack Orchestration (Heat) system. </p>

            <p><span>CLC</span> comes with predefined Heat orchestration templates (HOT). As part of the cluster setup, Heat is used to provision the VMs and configure the node operating system (CentOS). The preassembled base image for the nodes in the cluster is an <a href="http://www.projectatomic.io/" target="_blank"><u>Atomic</u></a> host. This is a node with a lean operating system designed to run Docker containers, built from upstream CentOS. It provides all the benefits of upstream distribution, plus the ability to perform Atomic upgrades and rollbacks.</p>

            <p>Heat is responsible for the actual creation of the resources as well as the installation and configuration of Kubernetes (Cluster Orchestration) on top of them.</p>

        </div>

    </div>


</body>
</html>
