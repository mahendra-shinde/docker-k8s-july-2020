## Creating Kubernetes API Objects using Declaration deployment (YAML)

1. Create a new YAML file with name 'mynamespace.yml'

```yml
apiVersion: v1
kind: Namespace
metadata: 
  name: mahendra
```

2. Create namespace and TEST it

```
$ kubectl apply -f mynamespace.yml
###Old Alternative: kubectl create -f mynamespace.yml
$ kubectl get ns
```