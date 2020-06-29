<center>
<h1>Google Cloud Platform - Notes</h1>
</center>

## Creating NGINX Server

Following commands are useful for installing nginx server on a virtual machine  
`apt-get install nginx -y`

Check the installation  
`ps auwx |grep nginx`

Output should be like below:

<center>
<img src="images/nginx.png" />
</center>

##### NGINX Server is installed and should be running!

## Create a Virtual Machine Instance with GCloud CLI

To create a VM Instance, run:  
`gcloud compute instances create --machine-type [machine-type] --zone [zone]`

e.g: `gcloud compute instances create gcelab2 --machine-type n1-standard-2 --zone us-central1-c`  
Virtaul Machine should be up and running!

#### Set Default Zone and Machine Type

`gcloud config set compute/zone ...`

`gcloud config set compute/region ...`

After this, you don't need to use `--zone` flag every time

## List resources

To list the `gcloud` resources, use followign commands  
`gcloud [resource-name] list`  
e.g: `gcloud config list` or `gcloud compute instaces list`

## SSH a Virtual Machine

To connect with a VM through SSH, use:  
`gcloud compute ssh [name-of-vm] --zone [--zone-of-vm]`

e.g: `gcloud compute ssh gcelab2 --zone us-central1-c`

## Enter Interactive Mode

gcloud interactive has auto prompting for commands and flags, and displays inline help snippets in the lower section as the command is typed.

**Install the beta components**  
`sudo apt-get install google-cloud-sdk`
**Enter Interactive Mode**  
`gcloud beta interactive`

<center>
<h2>Using Google Kubernetes Engine</h2>
</center>
Google Kubernetes Engine (GKE) provides a managed environment for deploying, managing, and scaling your containerized applications using Google infrastructure. The Kubernetes Engine environment consists of multiple machines (specifically Google Compute Engine instances) grouped together to form a container cluster.

## Create a Kubernetes Engine Cluster

A cluster consists of at least one cluster master machine and multiple worker machines called nodes. Nodes are Compute Engine virtual machine (VM) instances that run the Kubernetes processes necessary to make them part of the cluster.  
To create cluster, run

`gcloud container clusters create [cluster-name]`

## Get Auth Credentials for the Cluster

After creating your cluster, you need to get authentication credentials to interact with the cluster.

`gcloud conatiner clusters get-credentials [cluster-name]`

**Now, cluster is ready to use! You can run Kubernetes**
