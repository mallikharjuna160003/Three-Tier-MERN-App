1. create an EC2 instance t2-micro type and a key pair
2. login to EC2 instance by 
```
ssh -i <key-pair> hostname@<ip-address>
```
3. Clone the git using git clone <repo-url>
4. create dockerfile Dockerfile in frontend app directory
```
FROM node:14
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
CMD ["npm","start"]
```
5. give permission for the current user to run docker without sudo
```
sudo chown $USER /var/run/docker.sock
```
6. Build the image
```
docker build -t three-tier-frontend .
```
7. Run the image 
```
docker run -d -p <hostport>:<container-port> -t three-tier-frontend
```
Check the running containers
```
$ docker ps
CONTAINER ID   IMAGE                        COMMAND                  CREATED         STATUS         PORTS                                       NAMES
1302bfd65102   three-tier-frontend:latest   "docker-entrypoint.s…"   8 minutes ago   Up 8 minutes   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp   beautiful_mcclintock
sunkara@sunkara-VivoBo
```
to deploy the images to AWS Elastic Container Registry we need AWS CLI

```curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip
unzip awscliv2.zip
sudo ./aws/install -i /usr/local/aws-cli -b /usr/local/bin --update

```
create an  IAM user in AWS and give AdministatorAccess Permissions and create Access Key
![image](https://github.com/mallikharjuna160003/Three-Tier-MERN-App/assets/74324685/d6e715a5-3d05-4583-a559-c614fe7ac1bc)

![image](https://github.com/mallikharjuna160003/Three-Tier-MERN-App/assets/74324685/6dca9490-88b0-4216-9615-d66a3e263b5f)


```
$aws configure
AWS Access Key ID [****************ULVW]: <Access Key ID>
AWS Secret Access Key [****************WOKk]: <Access Secret Key>
Default region name [us-west-1]: 
Default output format [json]:
```
Create an ECR repository
![image](https://github.com/mallikharjuna160003/Three-Tier-MERN-App/assets/74324685/d1dff2e4-d003-4147-9146-a3de283e40b1)

Run the pull commands

![image](https://github.com/mallikharjuna160003/Three-Tier-MERN-App/assets/74324685/c808f4b9-7db2-4581-ae66-424eeb54952d)

```
aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/d0f7g1k7
```

```
$ docker build -t three-tier-frontend .
[+] Building 6.4s (11/11) FINISHED                               docker:default
 => [internal] load build definition from Dockerfile                       0.0s
 => => transferring dockerfile: 129B                                       0.0s
 => [internal] load .dockerignore                                          0.0s
 => => transferring context: 468B                                          0.0s
 => [internal] load metadata for docker.io/library/node:14                 2.2s
 => [auth] library/node:pull token for registry-1.docker.io                0.0s
 => [1/5] FROM docker.io/library/node:14@sha256:a158d3b9b4e3fa813fa6c8c59  0.0s
 => [internal] load build context                                          1.6s
 => => transferring context: 268.04MB                                      1.6s
 => CACHED [2/5] WORKDIR /app                                              0.0s
 => CACHED [3/5] COPY package*.json .                                      0.0s
 => CACHED [4/5] RUN npm install                                           0.0s
 => [5/5] COPY . .                                                         1.1s
 => exporting to image                                                     1.3s
 => => exporting layers                                                    1.3s
 => => writing image sha256:5a34fd84571b9a1f8aa240f8efb3c1dbdc62bef6c3db7  0.0s
 => => naming to docker.io/library/three-tier-frontend                     0.0s

What's Next?
  View a summary of image vulnerabilities and recommendations → docker scout quickview
```
build the image 
```
$ docker tag three-tier-frontend:latest public.ecr.aws/d0f7g1k7/three-tier-frontend:latest
```
Push the image to ECR
```
docker push public.ecr.aws/d0f7g1k7/three-tier-frontend:latest
```
![image](https://github.com/mallikharjuna160003/Three-Tier-MERN-App/assets/74324685/b18e70c8-a7bb-4f5d-b2ae-7c54166a9d13)

Follow the same creating ECR repo for backend in AWS and build the image push to ECR
check the backend container logs it show error we are not yet connected the backend to Mongo
```
$ docker logs 7ba765dd8e33
Listening on port 3500...
Could not connect to database. MongooseError: The `uri` parameter to `openUri()` must be a string, got "undefined". Make sure the first parameter to `mongoose.connect()` or `mongoose.createConnection()` is a string.
    at NativeConnection.Connection.openUri (/app/node_modules/mongoose/lib/connection.js:694:11)
    at /app/node_modules/mongoose/lib/index.js:351:10
    at /app/node_modules/mongoose/lib/helpers/promiseOrCallback.js:32:5
    at new Promise (<anonymous>)
    at promiseOrCallback (/app/node_modules/mongoose/lib/helpers/promiseOrCallback.js:31:10)
    at Mongoose._promiseOrCallback (/app/node_modules/mongoose/lib/index.js:1149:10)
    at Mongoose.connect (/app/node_modules/mongoose/lib/index.js:350:20)
    at module.exports (/app/db.js:17:24)
    at Object.<anonymous> (/app/index.js:7:1)
    at Module._compile (internal/modules/cjs/loader.js:1114:14)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:1143:10)
    at Module.load (internal/modules/cjs/loader.js:979:32)
    at Function.Module._load (internal/modules/cjs/loader.js:819:12)
    at Function.executeUserEntryPoint [as runMain] (internal/modules/run_main.js:75:12)
    at internal/main/run_main_module.js:17:47

```
Install kubectl
```
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
kubectl version --short --client
```
Install EKSctl

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```
EKS cluster setup
```
eksctl create cluster --name three-tier-cluster --region us-west-2 --node-type t2.medium --nodes-min 2 --nodes-max 2
aws eks update-kubeconfig --region us-west-2 --name three-tier-cluster
kubectl get nodes
```

To create namespace
```
$kubectl create namespace workshop
namespace/workshop created
```

Create deployment
```
$ kubectl apply -f deployment.yaml  -n three-tier
deployment.apps/mongodb created
```
create secrets pod
```
 $ kubectl apply -f secrets.yaml  -n three-tier
secret/mongo-sec created

```
check the logs mongo pod
```
$ kubectl logs api-8d74f7f8f-5v8x7 -n three-tier
Listening on port 8080...
Connected to database.

```

Follow same for frotned backend and database manifest files
# install AWS Load Balancer

```
curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/install/iam_policy.json
aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam_policy.json
eksctl utils associate-iam-oidc-provider --region=us-west-2 --cluster=three-tier-cluster --approve
eksctl create iamserviceaccount --cluster=three-tier-cluster --namespace=kube-system --name=aws-load-balancer-controller --role-name AmazonEKSLoadBalancerControllerRole --attach-policy-arn=arn:aws:iam::626072240565:policy/AWSLoadBalancerControllerIAMPolicy --approve --region=us-west-2
```
# Deploy AWS Load Balancer
```
sudo snap install helm --classic
helm repo add eks https://aws.github.io/eks-charts
helm repo update eks
helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=my-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
kubectl get deployment -n kube-system aws-load-balancer-controller
```
expose the port

```
kubectl port-forward svc/api 8080:8080 -n three-tier
```
Final output::

![image](https://github.com/mallikharjuna160003/Three-Tier-MERN-App/assets/74324685/1903d28f-1387-4cd0-846a-31b8798d30ac)


