## Create a new application deployment using Declarative approach (All Kubernetes)

1. Test connectivity to cluster from kubectl

```
$ kubectl cluster-info
$ kubectl get nodes
```

2.  Deploy a sample application using Command:

```
$ kubectl apply -f https://raw.githubusercontent.com/mahendra-shinde/kubernetes-demos/master/09-deployment/deploy-1.yaml
## List all the pods
$ kubectl get pods
## Try to delete the first pod
# kubectl delete pod <PODNAME>
## Try to list pods again
$ kubectl get pods
```

3.  Scaling application deployment

```
$ kubectl scale deploy deploy1 --replicas=10
$ kubectl get pod
$ kubectl scale deploy deploy1 --replicas=2
$ kubectl get pod
```

4.  Clean Up

```
$ kubectl delete deploy deploy1
```