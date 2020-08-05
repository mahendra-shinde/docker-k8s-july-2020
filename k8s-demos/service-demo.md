# service demo

## Service Type: Cluster ip

1. Create a service file `myservice.yml`

```yml
apiVersion: v1
kind: Service
metadata:
  name: myservice
spec:
  ## DEFAULT SERVICE TYPE IS CLUSTER-IP
  selector:
    app: myweb
  ports:
  - port: 8080
    targetPort: 80
```

2. Check the service

```
$ kubectl get svc -o wide
## list endpoint of service
$ kubectl get ep myservice -o wide 
## compare pod ip to ep ip
$ kubectl get po -o wide
```

3. Test service from one of the pods

```
$ kubectl exec -it [PODNAME] sh
$ curl http://myservice:8080
$ exit
```

## Service Type: NodePort

1. Modify service definition 'myservice.yml'

```yml
apiVersion: v1
kind: Service
metadata:
  name: myservice
spec:
  ## DEFAULT SERVICE TYPE IS CLUSTER-IP
  type: NodePort
  selector:
    app: myweb
  ports:
  - port: 8080
    nodePort: 30001
    targetPort: 80
```

2. apply the changes

```
$ kubectl apply -f myservice.yml
$ kubectl describe svc myservice
```

3. Test service from one of the pods

```
$ kubectl get nodes -o wide
## get INTERNAL-IP of One of the Nodes
$ kubectl exec -it [PODNAME] sh
$ curl http://myservice:8080
$ curl http://[NODE-IP]:30001
$ exit
```

## Service Type: LoadBalancer

1. Modify service definition 'myservice.yml'

```yml
apiVersion: v1
kind: Service
metadata:
  name: myservice
spec:
  ## DEFAULT SERVICE TYPE IS CLUSTER-IP
  type: LoadBalancer
  selector:
    app: myweb
  ports:
  - port: 8080
    nodePort: 30001
    targetPort: 80
```

2. apply the changes

```
$ kubectl apply -f myservice.yml
$ kubectl describe svc myservice
```

3. Test service from one of the pods

```
## Get External IP
$ kubectl get svc myservice
## Get Node IPs
$ kubectl get nodes -o wide
## get INTERNAL-IP of One of the Nodes
$ kubectl exec -it [PODNAME] sh
$ curl http://myservice:8080
$ curl http://[NODE-IP]:30001
$ curl http://[EXTERNAL-IP]:8080
$ exit
```

4.  External Access using `http://localhost:8080` on docker-desktop or `http://[external-ip]:8080` on AKS
