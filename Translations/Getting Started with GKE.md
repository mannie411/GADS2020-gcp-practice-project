# Lab: Getting Started with Kubernetes Engine

## Overview
In this lab, you create a Google Kubernetes Engine cluster containing several containers, each containing a web server. You place a load balancer in front of the cluster and view its contents.

### Objectives
In this lab, you learn how to perform the following tasks:

 - Provision a Kubernetes cluster using Kubernetes Engine.

 - Deploy and manage Docker containers using kubectl.

## Start Lab: 

### Steps:

1. Sign in to the Google Cloud Platform (GCP) Console

 - Click Open Google Console.

 - Click Use another account and copy/paste credentials for this lab into the prompts.

 - Accept the terms and skip the recovery resource page.


2. Confirm that needed APIs are enabled

  > Make a note of the name of your GCP project. This value is shown in the top bar of the Google Cloud Platform Console. It will be of the form qwiklabs-gcp- followed by hexadecimal numbers.

 - In the GCP Console, on the Navigation menu (Navigation menu), click APIs & Services.

 - Scroll down in the list of enabled APIs, and confirm that both of these APIs are enabled:

    > Kubernetes Engine API
    > Container Registry API

 - If either API is missing, click Enable APIs and Services at the top. Search for the above APIs by name and enable each for your current project. (You noted the name of your GCP project above.)

3. Start a Kubernetes Engine cluster

 - In GCP console, on the top right toolbar, click the Open Cloud Shell button.

 - Cloud Shell icon

 - Click Continue. 

 - For convenience, place the zone that Qwiklabs assigned you to into an environment variable called MY_ZONE. At the Cloud Shell prompt, type this partial command:

    `export MY_ZONE=us-central1-a`

 - Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster webfrontend and configure it to run 2 nodes:

    `gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2`


 - After the cluster is created, check your installed version of Kubernetes using the kubectl version command:

    `kubectl version`

 - View your running nodes in the GCP Console. On the Navigation menu (Navigation menu), click Compute Engine > VM Instances.


4. Run and deploy a container

 - From your Cloud Shell prompt, launch a single instance of the nginx container. (Nginx is a popular web server.)

    `kubectl create deploy nginx --image=nginx:1.17.10`

 - View the pod running the nginx container:

    `kubectl get pods`

 - Expose the nginx container to the Internet:

    `kubectl expose deployment nginx --port 80 --type LoadBalancer`

 - View the new service:

    `kubectl get services`

 - Open a new web browser tab and paste your cluster's external IP address into the address bar. The default home page of the Nginx browser is displayed.

 - Scale up the number of pods running on your service:

    `kubectl scale deployment nginx --replicas 3`

 - Confirm that Kubernetes has updated the number of pods:

    `kubectl get pods`

 - Confirm that your external IP address has not changed:

    `kubectl get services`

 - Return to the web browser tab in which you viewed your cluster's external IP address. Refresh the page to confirm that the nginx web server is still responding.

 ## End Lab

