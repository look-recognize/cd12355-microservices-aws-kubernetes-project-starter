# Coworking Space Service Extension
By using microservice on AWS, this is a simple example about building a pipeline to deploy it in Kubernetes.
## Prerequiste
AWS usage(account, Codebuild, ECR, Cloudwatch), Kubernetes, GitHub, Docker
## Quick Started(Run the command below)
```
#Create kubernetes cluster on EKS
eksctl create cluster --name my-cluster --region us-east-1 --nodegroup-name my-nodes --node-type t3.small --nodes 1 --nodes-min 1 --nodes-max 2  
#Apply YAML configurations
kubectl apply -f pvc.yaml
kubectl apply -f pv.yaml
kubectl apply -f postgresql-deployment.yaml 
#ConfigMap and check the service
kubectl apply -f deployment/configmap.yaml
kubectl apply -f deployment/coworking.yaml
curl <BASE_URL>.us-east-1.elb.amazonaws.com:5153/health_check
curl <BASE_URL>.us-east-1.elb.amazonaws.com:5153/api/reports/daily_usage
curl <BASE_URL>.us-east-1.elb.amazonaws.com:5153/api/reports/user_visits 
```