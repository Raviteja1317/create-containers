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

 ll
* sudo mv minikube-linux-amd64 /usr/local/bin/minikube
![Screenshot 2024-11-20 220314](https://github.com/user-attachments/assets/e9135bf9-3e7a-4ac2-978a-0e9bedb39aed)
sudo chmod +x /usr/local/bin/minikube

* sudo minikube version

* sudo apt install curl wget apt-transport-https -y


* sudo curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
![Screenshot 2024-11-20 215333](https://github.com/user-attachments/assets/0a8d2331-ad7a-46db-aac2-38ddaa399316)

![Screenshot 2024-11-20 222936](https://github.com/user-attachments/assets/2f7333cb-320c-41d4-87b8-bcfdaa99eb9f)


*  aws s3api create-bucket --bucket ravi2025.local --region us-east-1

  

* sudo kubectl version --client

* sudo curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"

sudo echo "$(cat kubectl.sha256) kubectl" | sha256sum --check

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

sudo kubectl version --client

sudo kubectl version --client --output=yaml

sudo minikube start --driver=docker --force

creation of pod

kubectl run pod1 --image=nginx

kubectl get pods

