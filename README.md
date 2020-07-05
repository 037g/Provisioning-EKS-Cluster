# Project Summary
This repo contains code and documentation, detailing the design and development of two independent and multi-regional AWS EKS clusters that operate with BLUE/GREEN functionality.

## OBJECTIVES
### //Provisioning
- [x] Using Terraform and/or Ansible, deploy two kubernetes clusters across two separate public cloud regions. 
- [x] Use Global Load Balancing to route traffic between the two clusters
- [x] Configure the ability to direct users to specific application instances 
### //Deployment
- [x] Deploy a simple kubernetes based application across both clusters
- [ ] Automate the deployment of the application using any modern CI / CD tooling
of your choice
- [x] Perform blue/green routing to the application across both clusters
- [ ] BONUS​ - Automate the traffic routing through a GitOps approach

 	term
: definition 

The EKS cluster is provisioned with [eksctl](https://eksctl.io/) which used CloudFormation stacks to deploy.

## Requirments
Please ensure the following tools are installed. The project was developed/tested with the following versions.
- [awscli v2.0.25](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
- [ansible v2.9.10](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [eksctl v0.22.0](https://eksctl.io/)
- [pipenv](https://pypi.org/project/pipenv/)
- [python v3.7](https://www.python.org/downloads/)

Install python dependencies:
```
pipenv install -r requirements.txt
```


## Ansible Deployment Scripts
The Ansible Scripts should be run in the following order:

| Run Order  |  Description |
|-|-|
|  1_Build_Cluster.yml | Provisions the cluster with [eksctl v0.22.0](https://eksctl.io/).  |
|  2_Configure_Cluster.yml | Configures [ALB Ingress Controller v1.16](https://kubernetes-sigs.github.io/aws-alb-ingress-controller/) |
|  3_Deploy_App.yml |  Configures [External-DNS v0.7.2](https://github.com/kubernetes-sigs/external-dns) and Deploys Appliation >Ingress, Svc, Deployment | 
|  4_Blue_Green_Route53_Switch.yml |  Configures External DNS and Deploys Appliation (Ingress, Svc, Deployment) | 


