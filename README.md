This project demonstrates how to automate the creation and deletion of an Amazon EKS (Elastic Kubernetes Service) cluster using Jenkins CI/CD pipelines and Terraform.
The setup follows standard DevOps practices such as infrastructure validation, manual approval, and parameterized execution.
Tech Stack
AWS (EKS, EC2, IAM, VPC)
Jenkins
Terraform
Kubernetes (kubectl)
Ubuntu 22.04
Architecture Flow
Jenkins runs on an EC2 instance
Terraform provisions AWS infrastructure
Amazon EKS cluster is created
kubectl is used to interact with the cluster
Jenkins pipeline supports both apply and destroy actions
Prerequisites
AWS account
IAM user with required permissions
EC2 instance (Ubuntu 22.04)
Jenkins installed
Terraform installed
kubectl installed
AWS CLI configured
Repository Structure
.
├── eks.tf
├── vpc.tf
├── provider.tf
├── guide.txt
└── README.md
Jenkins Pipeline Features
Source code checkout from GitHub
Terraform initialization
Terraform validation
Terraform plan with manual approval
Parameterized execution (apply or destroy)
Pipeline Parameters
action
apply → creates EKS infrastructure
destroy → deletes EKS infrastructure
Terraform Workflow
terraform init
terraform validate
terraform plan
terraform apply
terraform destroy
Accessing the EKS Cluster
After successful deployment, configure kubeconfig:
aws eks update-kubeconfig --region ap-south-1 --name <ClusterName>
Test the cluster:
kubectl run nginx --image=nginx
kubectl get pods
Cleanup
To destroy the infrastructure:
Trigger Jenkins pipeline
Select destroy parameter
Run the job
Terminate the EC2 instance after completion
