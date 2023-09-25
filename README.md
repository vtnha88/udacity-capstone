# Cloud DevOps Engineer Capstone Project

This project signifies the triumphant culmination of my final Capstone project and the successful conclusion of the Cloud DevOps Engineer Nanodegree program at Udacity.

## What did I learn?

In this project, I harnessed the expertise and insights I cultivated during the Cloud DevOps Nanodegree program. This encompassed a spectrum of proficiencies, such as:
- Leveraging Circle CI to orchestrate Continuous Integration and Continuous Deployment workflows.
- Constructing robust pipelines for streamlined development and deployment.
- Proficiently wielding Ansible and CloudFormation for the deployment of resilient clusters.
- Mastering the art of crafting Kubernetes clusters with precision.
- Seamlessly integrating Docker containerization into the pipeline process.
- Navigating the AWS ecosystem with dexterity and proficiency.

## Application

The Application is based on a python3 script using <a target="_blank" href="https://flask.palletsprojects.com">flask</a> to render a simple webpage in the user's browser.
A requirements.txt is used to ensure that all needed dependencies come along with the Application.

## Kubernetes Cluster

I used AWS CloudFormation to deploy the Kubernetes Cluster.
The CloudFormation Deployment can be broken down into four Parts:
- **Networking**, to ensure new nodes can communicate with the Cluster
- **Elastic Kubernetes Service (EKS)** is used to create a Kubernetes Cluster
- **NodeGroup**, each NodeGroup has a set of rules to define how instances are operated and created for the EKS-Cluster
- **Management** is needed to configure and manage the Cluster and its deployments and services. I created two management hosts for extra redundancy if one of them fails.

## CircleCi - CI/CD Pipelines

I used CircleCi to create a CI/CD Pipeline to test and deploy changes manually before they get deployed automatically to the Cluster using Ansible.

## Linting using Pylint and Hadolint

Linting is used to check if the Application and Dockerfile is syntactically correct.
This process makes sure that the code quality is always as good as possible.

## Access the Application

After the EKS-Cluster has been successfully configured using Ansible within the CI/CD Pipeline, I checked the deployment and service as follows:

```
$ kubectl get deployments
NAME                          READY   UP-TO-DATE   AVAILABLE   AGE
capstone-project-deployment   4/4     4            4           68m

$ kubectl get services
NAME                       TYPE           CLUSTER-IP       EXTERNAL-IP                                                                  PORT(S)        AGE
capstone-project-service   LoadBalancer   10.100.240.221   a9d7166a2525d405db00907ffb57de4e-1479088191.eu-central-1.elb.amazonaws.com   80:32299/TCP   69m
kubernetes                 ClusterIP      10.100.0.1       <none>                                                                       443/TCP        80m
```

Public LB DNS: http://a9d7166a2525d405db00907ffb57de4e-1479088191.eu-central-1.elb.amazonaws.com

![Access LB DNS](./screenshots/access_lb_dns_demo.PNG)
