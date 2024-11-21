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
   
   ![Screenshot 2024-11-20 234622](https://github.com/user-attachments/assets/620b100b-4be7-4f14-8cb8-71d6d0a3d43d)

  # Create the Kubernetes cluster with the updated state and configuration
kops create cluster \
    --name=ravi.com \
    --state=s3://ravi2025.local \
    --zones=us-east-1a \
    --control-plane-size=t2.micro \
    --node-size=t2.micro

kops get cluster --name ravi.com --state=s3://ravi2025.local
kops update cluster --name ravi.com --state=s3://ravi2025.local --control-plane-size t2.micro --yes

*  s3 bucket
*  ![Screenshot 2024-11-21 001027](https://github.com/user-attachments/assets/c5cd244d-524f-4075-b839-d6b1058b53c7)
  

*  Automatically create autoscaling

*  ![Screenshot 2024-11-20 000032](https://github.com/user-attachments/assets/c40870b9-dbda-4926-8554-bf8321e03842)
  

   ![Screenshot 2024-11-20 002045](https://github.com/user-attachments/assets/b40431a9-041d-4c28-bf9a-afb26b6d2c13)

   * load balancer
   * ![Screenshot 2024-11-20 000014](https://github.com/user-attachments/assets/f62969f3-34ec-4f9c-9019-7ea96b1342e0)
 
   * vi ravi.yml
     
   apiVersion: v1
   
   kind: Pod
   
 metadata:
 
  name: kops-pod
  
spec:

  containers:
  
    - name: ravi
    
      image: nginx
      
      ports:
      
      - containerPort: 80
      
    - name: vinod12
    
      image: ubuntu
      
      command: ["sh", "-c", "while true; do echo 'welcome to skywaves'; sleep 10; done"]
      
  :wq!
  
![Screenshot 2024-11-21 093943](https://github.com/user-attachments/assets/8c935476-f8a8-457f-8889-0a6b4ba5f929)












