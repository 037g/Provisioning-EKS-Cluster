# EKS-Cluster-Provisioning
This repo contains Ansible scrips to standup two AWS EKS cluster (Blue/Green).

The EKS cluster is provisioned with [eksctl](https://eksctl.io/) which used CloudFormation stacks to deploy.

## Requirments
Please ensure the following tools are installed:
- [awscli](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
- [ansible](https://www.ansible.com/)
- [eksctl](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html)
- [pipenv](https://pypi.org/project/pipenv/)
- [python > 3.6](https://www.python.org/downloads/)

Install python dependencies:
```
pipenv install -r requirements.txt
```


## Ansible Scripts
The Ansible Scripts should be run in the following order:

| Run Order  |  Description |
|:-:|:-:|
|  main.yml | Provisions the cluster.  |
|  configure_cluster.yml | Configures ALB Ingress Controller |
|  deploy_app.yaml |  Configures External DNS and Deploys Appliation (Ingress, Svc, Deployment) | 


