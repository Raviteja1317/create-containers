# create-containers

* create the ec2 instance 
  
* increase the volume size up to 20
![Screenshot 2024-11-20 211812](https://github.com/user-attachments/assets/c077ccc1-ac1e-40c0-a369-ebf0636587cb)

* apt update -y

* sudo curl -fsSL https://get.docker.com -o get-docker.sh

* ll
* chmod 700 get-docker.sh

* ./get-docker.sh

* docker version

* systemctl status docker

* sudo curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 


![Screenshot 2024-11-20 220314](https://github.com/user-attachments/assets/e9135bf9-3e7a-4ac2-978a-0e9bedb39aed)
sudo chmod +x /usr/local/bin


* sudo curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
![Screenshot 2024-11-20 215333](https://github.com/user-attachments/assets/0a8d2331-ad7a-46db-aac2-38ddaa399316)

![Screenshot 2024-11-20 222936](https://github.com/user-attachments/assets/2f7333cb-320c-41d4-87b8-bcfdaa99eb9f)


*  aws s3api create-bucket --bucket ravi2025.local --region us-east-1
  ![Screenshot 2024-11-20 234450](https://github.com/user-attachments/assets/a668f123-db67-41a5-b64e-ef387664851c)

* aws s3api put-bucket-versioning --bucket ravi2025.local   --versioning-configuration Status=Enabled

* export NAME=ravi2025.example.com

* export KOPS_STATE_STORE=s3://ravi2025.local-state-store

* Create cluster configuration

* We will need to note which availability zones are available to us.  we will be deploying our cluster to the us-east-1 region.

 * aws ec2 describe-availability-zones --region us-east-1

 * kops create cluster \
    --name=${NAME} \
    --cloud=aws \
    --zones=us-west-2a \
    --discovery-store=s3://ravi2025.local
   
   ![Screenshot 2024-11-20 234622](https://github.com/user-attachments/assets/620b100b-4be7-4f14-8cb8-71d6d0a3d43d)


* sudo kubectl version --client

* sudo curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"

 sudo echo "$(cat kubectl.sha256) kubectl" | sha256sum --check

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

sudo kubectl version --client

sudo kubectl version --client --output=yaml

*  s3 bucket
*  ![Screenshot 2024-11-21 001027](https://github.com/user-attachments/assets/c5cd244d-524f-4075-b839-d6b1058b53c7)








