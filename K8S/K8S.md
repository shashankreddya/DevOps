## Steps to install Kubernetes on AWS using KOPS (Ubuntu instance)

1. Create Ubuntu EC2 instance

2. Install AWSCLI

 curl https://s3.amazonaws.com/aws-cli/awscli-bundle.zip -o awscli-bundle.zip
 apt install unzip python
 unzip awscli-bundle.zip
 #sudo apt-get install unzip - if you dont have unzip in your system
 ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws

3. Install kubectl on ubuntu instance

 curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
 chmod +x ./kubectl
 sudo mv ./kubectl /usr/local/bin/kubectl
 
4. Install kops on ubuntu instance

 curl -LO  https://github.com/kubernetes/kops/releases/download/1.15.0/kops-linux-amd64
 chmod +x kops-linux-amd64
 sudo mv kops-linux-amd64 /usr/local/bin/kops
 kops version (it should be 1.15.0)
 
 5. Create an IAM user/role with Route53, EC2, IAM and S3 full access
 
 6. Attach IAM role to ubuntu instance
 
aws configure

7. Create a Route53 private hosted zone

8. Create an S3 bucket

9. export KOPS_STATE_STORE=s3://my-k8s-demo-bucket

10. Create sshkeys before creating cluster

ssh-keygen

11. Create kubernetes cluster definitions on S3 bucket

kops create cluster --cloud=aws --zones=us-east-2a,us-east-2b --name=latestoffcampus.com --dns private --state=s3://my-k8s-demo-bucket --master-count=1 --master-size=t2.micro --node-count=2 --node-size=t2.micro

12. Create kubernetes cluser
 
 kops update cluster --name latestoffcampus.com --yes --admin
 
 Commands
 
 kops validate cluster
 
 kops delete cluster <cluster_name> --yes
 
 Troubleshooting
 
 ELB access is not granted with AdminAccess, if kops throws an error then role can be added by running following command
 
aws iam create-service-linked-role --aws-service-name elasticloadbalancing.amazonaws.com
