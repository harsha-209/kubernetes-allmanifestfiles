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

Replicaset-commands

kubectl get replicaset
kubectl get replicaset <nameof replicaset>
kubectl edit replicaset <name of replicaset>
kubectl set image rs test-replicaset php-redis=nginx:1.7.9
kubectl scale -replicas=6 -f <manifestfile>
kubectl scale -replicas=5 replicaset <nameof replicaset>
kubectl delte replicaset <name of replicaset>
