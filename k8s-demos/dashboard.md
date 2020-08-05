# Kubernetes Dashboard (WebUI)

## Installing Dashboard on docker-desktop or on-premise k8s

1. You need to deploy custom dashboard YML artifact

```
$ kubectl apply -f https://raw.githubusercontent.com/mahendra-shinde/kubernetes-demos/master/dashboard.yaml

$ kubectl get all -n kubernetes-dashboard
```

2.  You need to get secret token

```
## List all the secrets
$ kubectl get secret -n kubernetes-dashboard
## find name of secret which begins with 'kubernets-dashbard-token-'
$ kubectl describe secrets kubernetes-dashboard-token-fmdbx -n kubernetes-dashboard
## Copy the TOKEN (Last Field)
```

3.  Start the KUBECTL PROXY 

```
$ kubectl proxy 
```

4.  Visit following URL in web-browser
    http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy


5.  Dashboard would prompt you to enter TOKEN, just copy-paste the token value, click "Login" or "Sign In"



* Dashboard is installed by-default in AKS and Its URL is
    http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=default

* Dashboard on Docker-Desktop is NOT Installed. And when you install it
    the URL would be
    http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=default

* Dasboard is ACCESSIBLE on "localhost:8001" only after you use following command:

```
$ kubectl proxy 
```

* Dashboard uses SECRET TOKEN for authentication, use following command:

```
## For AKS
$ kubectl get secrets -n kube-system
## OnPremise
$ kubectl get secrets -n kubernetes-dashboard

## search for secret with name 'kubernetes-dashboard-token-XXXXX'
## Use token name and namespace to get TOKEN
$ kubectl describe secret kubernetes-dashboard-token-s6bfz -n kube-system

## Start the KUBE PROXY Server
$ kubectl proxy
```

* Access your dashboard using URL 
    AKS: http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=default

    Other: http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/overview?namespace=default

* Use Login Option "Token" and copy-paste the token. click "Log in".

* At this point DASHBOARD doesn't have required privileges to connect cluster.

