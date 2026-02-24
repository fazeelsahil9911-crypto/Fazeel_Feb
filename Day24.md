# Day 24 - Advanced Terraform Modules and CI/CD Pipeline Scaling

##    Ansible - Deploy Docker Containers with Kubernetes Using Helm

'''yaml
- name: Deploy Docker Containers with Helm
  hosts: localHost
  tasks:
    - name: Install Helm
      command: curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
    - name: Deploy microservices with Helm
      command: helm install pathnex-app ./microservice-chart
   Terraform - Multi-Mudule Infrastructure with Outputs
module "pathnex_vpc" {
  source = "./vpc"
}

module "pathnex_instance" {
  source = "./instance"
  vpc_id = module.pathnex_vpc.vpc_id
}

output "instance_id" {
  value = module.pathnex_instance.instance_id
}
    Kubernetes - Helm-based Auto-Scaling Deployments
apiVersion: apps/v1
kind: Deployment
metadata:
  name: pathnex-web-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: pathnex-web-app
  template:
    metadata:
      lablels:
        app: pathnex-web-app
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80
---
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: pathnex-web-app-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: pathnex-web-app
  minReplicas: 2
  maxReplicas: 10
  targetCPUUtilizationPercantage: 80
    Jenkinsfile - Scaling CI/CD Pipeline
pipeline {
    agent any
    stages {
        stage('Scale Up') {
            steps {
                echo 'Scaling up Jenkins pipeline agents for heavy workloads.
                // Simulating scaling logic
            }
         }
         stage('Build') {
             steps {
                 echo 'Building prject...'
             }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying project...'
            }
        }
    }
}
