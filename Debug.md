# Debug
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ eksctl delete iamserviceaccount --cluster=demo-cluster --name=aws-load-balancer-controller --namespace=kube-system
Error: unable to describe cluster control plane: operation error EKS: DescribeCluster, https response error StatusCode: 404, RequestID: 90a4954a-83fd-45f5-a8c4-c2d78b7184a3, ResourceNotFoundException: No cluster found for name: demo-cluster.
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
Error: INSTALLATION FAILED: cannot re-use a name that is still in use
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl get deployment -n kube-system aws-load-balancer-controller
NAME                           READY   UP-TO-DATE   AVAILABLE   AGE
aws-load-balancer-controller   0/2     0            0           69m
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl delete deployment -n kube-system aws-load-balancer-controller
deployment.apps "aws-load-balancer-controller" deleted
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
Error: INSTALLATION FAILED: cannot re-use a name that is still in use
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl delete deployment -n kube-system aws-load-balancer-controller
Error from server (NotFound): deployments.apps "aws-load-balancer-controller" not found
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
Error: INSTALLATION FAILED: cannot re-use a name that is still in use
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller-2 eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
Error: INSTALLATION FAILED: Unable to continue with install: Secret "aws-load-balancer-tls" in namespace "kube-system" exists and cannot be imported into the current release: invalid ownership metadata; annotation validation error: key "meta.helm.sh/release-name" must equal "aws-load-balancer-controller-2": current value is "aws-load-balancer-controller"
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller-2 eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
Error: INSTALLATION FAILED: Unable to continue with install: Secret "aws-load-balancer-tls" in namespace "kube-system" exists and cannot be imported into the current release: invalid ownership metadata; annotation validation error: key "meta.helm.sh/release-name" must equal "aws-load-balancer-controller-2": current value is "aws-load-balancer-controller"
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller-2 eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
Error: INSTALLATION FAILED: Unable to continue with install: Secret "aws-load-balancer-tls" in namespace "kube-system" exists and cannot be imported into the current release: invalid ownership metadata; annotation validation error: key "meta.helm.sh/release-name" must equal "aws-load-balancer-controller-2": current value is "aws-load-balancer-controller"
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller-2 eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws^Coad-balancer-controller
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ cat ~/.aws/config 
[default]
region = us-west-1
output = json
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ cat ~/.aws/config 
[default]
region = us-west-1
output = json
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ cat ~/.aws/config ^C
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl delete secret aws-load-balancer-tls -n kube-system
secret "aws-load-balancer-tls" deleted
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller-2 eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
Error: INSTALLATION FAILED: Unable to continue with install: Service "aws-load-balancer-webhook-service" in namespace "kube-system" exists and cannot be imported into the current release: invalid ownership metadata; annotation validation error: key "meta.helm.sh/release-name" must equal "aws-load-balancer-controller-2": current value is "aws-load-balancer-controller"
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl edit secret aws-load-balancer-tls -n kube-system
Error from server (NotFound): secrets "aws-load-balancer-tls" not found
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller-2 eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller --set aws.loadBalancerController.service.annotations."service\.beta\.kubernetes\.io/aws-load-balancer-ssl-cert"=""
Error: INSTALLATION FAILED: Unable to continue with install: Service "aws-load-balancer-webhook-service" in namespace "kube-system" exists and cannot be imported into the current release: invalid ownership metadata; annotation validation error: key "meta.helm.sh/release-name" must equal "aws-load-balancer-controller-2": current value is "aws-load-balancer-controller"
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl delete secret aws-load-balancer-tls -n kube-system --force
Warning: Immediate deletion does not wait for confirmation that the running resource has been terminated. The resource may continue to run on the cluster indefinitely.
Error from server (NotFound): secrets "aws-load-balancer-tls" not found
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller-2 eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
Error: INSTALLATION FAILED: Unable to continue with install: Service "aws-load-balancer-webhook-service" in namespace "kube-system" exists and cannot be imported into the current release: invalid ownership metadata; annotation validation error: key "meta.helm.sh/release-name" must equal "aws-load-balancer-controller-2": current value is "aws-load-balancer-controller"
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl get all -n kube-system
NAME                          READY   STATUS    RESTARTS   AGE
pod/aws-node-4f7sd            2/2     Running   0          4h20m
pod/aws-node-zqll5            2/2     Running   0          4h20m
pod/coredns-9556476b9-9qkwl   1/1     Running   0          4h27m
pod/coredns-9556476b9-jvkw4   1/1     Running   0          4h27m
pod/kube-proxy-5sdf4          1/1     Running   0          4h20m
pod/kube-proxy-xgfkn          1/1     Running   0          4h20m

NAME                                        TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)         AGE
service/aws-load-balancer-webhook-service   ClusterIP   10.100.228.240   <none>        443/TCP         87m
service/kube-dns                            ClusterIP   10.100.0.10      <none>        53/UDP,53/TCP   4h27m

NAME                        DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
daemonset.apps/aws-node     2         2         2       2            2           <none>          4h27m
daemonset.apps/kube-proxy   2         2         2       2            2           <none>          4h27m

NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/coredns   2/2     2            2           4h27m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/coredns-9556476b9   2         2         2       4h27m
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl get deployment -n kube-system
NAME      READY   UP-TO-DATE   AVAILABLE   AGE
coredns   2/2     2            2           4h27m
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm list -n kube-system
NAME                        	NAMESPACE  	REVISION	UPDATED                               	STATUS  	CHART                             	APP VERSION
aws-load-balancer-controller	kube-system	1       	2024-02-09 01:15:40.07969363 +0530 IST	deployed	aws-load-balancer-controller-1.7.0	v2.7.0     
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm delete aws-load-balancer-controller -n kube-system
release "aws-load-balancer-controller" uninstalled
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl get all -n kube-system
NAME                          READY   STATUS    RESTARTS   AGE
pod/aws-node-4f7sd            2/2     Running   0          4h24m
pod/aws-node-zqll5            2/2     Running   0          4h24m
pod/coredns-9556476b9-9qkwl   1/1     Running   0          4h30m
pod/coredns-9556476b9-jvkw4   1/1     Running   0          4h30m
pod/kube-proxy-5sdf4          1/1     Running   0          4h24m
pod/kube-proxy-xgfkn          1/1     Running   0          4h24m

NAME               TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)         AGE
service/kube-dns   ClusterIP   10.100.0.10   <none>        53/UDP,53/TCP   4h30m

NAME                        DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
daemonset.apps/aws-node     2         2         2       2            2           <none>          4h30m
daemonset.apps/kube-proxy   2         2         2       2            2           <none>          4h30m

NAME                      READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/coredns   2/2     2            2           4h30m

NAME                                DESIRED   CURRENT   READY   AGE
replicaset.apps/coredns-9556476b9   2         2         2       4h30m
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm cache clean
Error: unknown command "cache" for "helm"
Run 'helm --help' for usage.
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/install/iam_policy.json
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  8386  100  8386    0     0   8013      0  0:00:01  0:00:01 --:--:--  8017
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam_policy.json

An error occurred (EntityAlreadyExists) when calling the CreatePolicy operation: A policy called AWSLoadBalancerControllerIAMPolicy already exists. Duplicate names are not allowed.
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ aws iam delete-policy --policy-arn arn:aws:iam::<account-id>:policy/AWSLoadBalancerControllerIAMPolicy  
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam_policy.json
{
    "Policy": {
        "PolicyName": "AWSLoadBalancerControllerIAMPolicy",
        "PolicyId": "ANPAXYSX5JZB3CFPYMCGO",
        "Arn": "arn:aws:iam::<account-id>:policy/AWSLoadBalancerControllerIAMPolicy",
        "Path": "/",
        "DefaultVersionId": "v1",
        "AttachmentCount": 0,
        "PermissionsBoundaryUsageCount": 0,
        "IsAttachable": true,
        "CreateDate": "2024-02-08T21:21:35+00:00",
        "UpdateDate": "2024-02-08T21:21:35+00:00"
    }
}
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ eksctl utils associate-iam-oidc-provider --region=us-west-2 --cluster=three-tier-cluster --approve
2024-02-09 02:51:50 [ℹ]  IAM Open ID Connect provider is already associated with cluster "three-tier-cluster" in "us-west-2"
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ eksctl create iamserviceaccount --cluster=three-tier-cluster --namespace=kube-system --name=aws-load-balancer-controller --role-name AmazonEKSLoadBalancerControllerRole --attach-policy-arn=arn:aws:iam::<account-id>:policy/AWSLoadBalancerControllerIAMPolicy --approve --region=us-west-2
2024-02-09 02:52:43 [ℹ]  1 iamserviceaccount (kube-system/aws-load-balancer-controller) was included (based on the include/exclude rules)
2024-02-09 02:52:43 [!]  serviceaccounts that exist in Kubernetes will be excluded, use --override-existing-serviceaccounts to override
2024-02-09 02:52:43 [ℹ]  1 task: { 
    2 sequential sub-tasks: { 
        create IAM role for serviceaccount "kube-system/aws-load-balancer-controller",
        create serviceaccount "kube-system/aws-load-balancer-controller",
    } }2024-02-09 02:52:43 [ℹ]  building iamserviceaccount stack "eksctl-three-tier-cluster-addon-iamserviceaccount-kube-system-aws-load-balancer-controller"
2024-02-09 02:52:43 [ℹ]  deploying stack "eksctl-three-tier-cluster-addon-iamserviceaccount-kube-system-aws-load-balancer-controller"
2024-02-09 02:52:45 [ℹ]  waiting for CloudFormation stack "eksctl-three-tier-cluster-addon-iamserviceaccount-kube-system-aws-load-balancer-controller"
2024-02-09 02:53:19 [ℹ]  waiting for CloudFormation stack "eksctl-three-tier-cluster-addon-iamserviceaccount-kube-system-aws-load-balancer-controller"
2024-02-09 02:53:21 [ℹ]  created serviceaccount "kube-system/aws-load-balancer-controller"
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm repo update eks
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "eks" chart repository
Update Complete. ⎈Happy Helming!⎈
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
NAME: aws-load-balancer-controller
LAST DEPLOYED: Fri Feb  9 02:54:23 2024
NAMESPACE: kube-system
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
AWS Load Balancer controller installed!
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ kubectl get deployment -n kube-system
NAME                           READY   UP-TO-DATE   AVAILABLE   AGE
aws-load-balancer-controller   2/2     2            2           26s
coredns                        2/2     2            2           4h39m
sunkara@sunkara-VivoBook:~/Documents/MERN-3-tier/TWSThreeTierAppChallenge/Kubernetes-Manifests-file$ 

