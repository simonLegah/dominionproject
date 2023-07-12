# Terraform and Ansible
I have used terraform as an Infrastructure as code (IaC) tool to provision my infrasctructure on AWS. Provisioned infrastructure inlude;
VPCs, EKS Clusters, Private and Public subnets, Iinternet Gateway, Routing Tables, SECURITY GROUP, etc.
https://github.com/WinifredZenabuin/UnityProject/blob/master/CI-CD%20Intergration.JPG
# EKS Getting Started Guide Configuration

This is the full configuration from https://www.terraform.io/docs/providers/aws/guides/eks-getting-started.html

See that guide for additional information.

NOTE: This full configuration utilizes the [Terraform http provider](https://www.terraform.io/docs/providers/http/index.html) to call out to icanhazip.com to determine your local workstation external IP for easily configuring EC2 Security Group access to the Kubernetes servers. 

# Provision EKS Infrastructure on AWS using Terraform
terraform init
terraform plan
terraform apply
terraform destory

# Jenkins
Jenkins will enable us to achieve Continuos Integration and Continuous Deployment. Our Jenkins pipeline-script  will ensure once the application is developed or modified it is automatically build using maven, tested using selenium, validated using SonarQube. The build artifacts will be uploaded to Nexus Private aritifact repository. 
# GitHub
The scripts used for this project can be clone from https://github.com/WinifredZenabuin/UnityProject.
I also confihured github-webhook so that ounce the source code is modified jenkins will srtigger a build.  
# Dockerfile
we are also using the created package (artifacts) to create a docker imgae for our application. Here docker is used for containerisation.  
```docker
docker build -t legah2045/springboot-app .
```
# Kubernetes Manifest files
This files will deploy a "Spring-boot-app" with a MongoDB. Our application and database is deployed using Replicat Set, ConFigMap, Ingress Controller, Secrets, PVC, StorageClass, HPA, and Cluster-Auto-Scaling.
We have also deployed Grafana and Prometheus using Helm Charts. This will monitor our applications, send alerts and as such we are going to achieve high availability.
```t
kubectl create deployment autoscaler-demo --image=nginx
kubectl get pods --all-namespaces | grep Running | wc -l
kubectl get nodes -o yaml | grep pods
kubectl scale deployment autoscaler-demo --replicas=20
```

# Build Project Using Maven

Maven is java based build tool to generate executable 

packages(jar, ear,war) for java based projects.

```bash
mvn clean package
```

## Create Docker Image
Docker is a continerization tool.Using docker we can deploy our applications as 

containers using docker images. Containers contains application code and also the softwares,

config files whatever is required for our application to run.

Create docker image using Dockerfile


```docker
docker build -t legah2045/springboot-app .
```

## Deploy Application Using EKS Cluster 

```kubectl apply 
kubectl apply -f springboot-app-deployment.yml
```

## List Docker Containers
```docker
docker ps -a
```

## License
[Winifred Zenabuin](https://www.linkedin.com/in/winifred-zenabuin-1b430b194/)
