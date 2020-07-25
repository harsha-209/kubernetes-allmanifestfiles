# kubernetes-allmanifestfiles

kubernetes-commands

kubectl get nodes
kubectl get pods
kubectl get -n <namespace>
kubectl describe pod <podname>
kubectl delete pod <podname>
kubectl edit pod <podname>
kubectl run nginx  --image=nginx
kubectl apply -f <manifestfile>
kubectl delet -f <manifestfile>
kubectl run <nameofpod>  --image=nginx   --dry-run=client -o yaml > pod.yaml #it creates a manifest file for kind is pod
kubectl run custom-nginx --image=nginx --port=8080

Replicaset-commands

kubectl get replicaset
kubectl get replicaset <nameof replicaset>
kubectl edit replicaset <name of replicaset>
kubectl set image rs test-replicaset php-redis=nginx:1.7.9
kubectl scale -replicas=6 -f <manifestfile>
kubectl scale -replicas=5 replicaset <nameof replicaset>
kubectl delete replicaset <name of replicaset>
  
  
Deployment-commands
kubectl get deployment
kubectl edit deployment <deploymentname>
kubectl get deployment <nameof deploymet>
kubectl create deployment <nameof deployment>  --image=nginx  #creating a deployment
to scale up
kubectl scale deployment <name of deployment> --replicas=2
  
  
Namespace
kubectl run <nameof pod> --image=redis -n <namespace>
kubectl get namespace
kubectl get pods -n <namespace>
kubectl create namespace <name ofnamespace>
kubeclt get pods <nameofpod> -n <particularnamespace>
  
service

kubectl get svc
kubectl get svc <nameof svc>
kubectl describe svc <name of svc>
suppose to if your deployment is cluster .then how to change into Nodeport
kubectl expose deployment  <name of deployment>  --type=NodePort  --target-port=8080 --name=my-servic --dry-run=client -o yaml > servic.yaml #it creates a new manifest file
  
  
imperative commands
 kubectl run redis --image=redis:alpine -l tier=db
 kubectl run nginx --image=redis 
 kubectl run redis --image=redis:alpine -l tier=db  --dry-run=client -o yaml > pod.yaml
 kubectl expose pod redis --port=6379 --name redis-service
 kubectl expose pod  <name of pod> --port=8080 --type=NodePort  --name=my-servic
 kubectl run custom-nginx --image=nginx --port=8080
 kubectl create deployment redis-deploy --image redis --namespace=dev-ns
 kubectl scale deployment redis-deploy --replicas=2 -n dev-ns
 kubectl create deployment redis-deploy --image redis --namespace=dev-ns --dry-run=client -o yaml > deploy.yaml
 kubectl run httpd --image=httpd:alpine --port=80 --expose
  
  
  
selctors and labes

kubectl get pods --selector env=dev | wc 
'kubectl get all --selector env=prod,bu=finance,tier=frontend



taints
#how to check any taint is available or not (taint means which does not allow to lanuch a pod)
kubectl describe node node01 | grep -i taints
kubectl taint nodes node01 spray=mortein:NoSchedule # creating a taint
kubectl taint nodes node01 spray=mortein:NoSchedule-
kubectl taint nodes node1 key=value:NoSchedule
kubectl taint nodes node1 key:NoSchedule-


labes
kubectl label nodes node01 clour=blue
# we can see lables by discribe nodes
kubectl describe nodes node01


static pods
create a manifest file and place it in /etc/kubernets/manifestfile
then it run that pods continously in master
suppose if a static pods runs in kubernetes node
ssh into that node and to delete that pod
delete manifest file in /var/lib/kublet/config.yaml


metric server to install on kubernets master

use this link
https://github.com/kodekloudhub/kubernetes-metrics-server

it takes some time to run and up
kubectl get pods
now to check which nodes consumes higest cpu
kubectl top node
kubectl top pods


logs
to see logs of pods
kubectl logs <name of pods>
if two containers in a pod then how to check logs for first containers
kubectl logs <name of pod> -c <containername>
  
