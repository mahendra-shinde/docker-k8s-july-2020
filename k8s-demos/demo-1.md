## Create a new application deployment using Imperative approach (Docker Desktop)

1. Test connectivity to cluster from kubectl

```
$ kubectl cluster-info
$ kubectl get nodes
```

2.  Deploy a sample application using Command:

```
$ kubectl run myapp --image=mahendrshinde/myweb --replicas=3
## List all the pods
$ kubectl get pods
## Try to delete the first pod
# kubectl delete pod <PODNAME>
## Try to list pods again
$ kubectl get pods
```

3.  Scaling application deployment

```
$ kubectl scale deploy myapp --replicas=10
$ kubectl get pod
$ kubectl scale deploy myapp --replicas=2
$ kubectl get pod
```

4.  Clean Up

```
$ kubectl delete deploy myapp
```