## Rolling Update

1. Deploy the initial application with image 'mahendrshinde/myweb:1'

```
$ kubectl apply -f mydeploy.yml
```

2.  Open a new CMD / Powershell and keep this command running:

```
$ kubectl get rs -o wide -w

```

3.  Open 'mydeploy.yml' and change the IMAGE from 'mahendrshinde/myweb:1' to ''mahendrshinde/myweb:2' and save the changes

```
$ kubectl apply -f mydeploy.yml
```

4.  Go back the CMD/PWSH window showing changes in ReplicaSet (refer step#2)

5.  Open 'mydeploy.yml' and change the IMAGE from 'mahendrshinde/myweb:2' to ''mahendrshinde/myweb:3' and save the changes

```
$ kubectl apply -f mydeploy.yml
```

6.  Repeat step #4 (Recheck the changes in replicaset)

7.  View the rollout history

```
$ kubectl rollout history deploy deploy1
```

8.  Undo the last deployment (will re-deploy version '2' of image)

```
$ kubectl rollout undo deploy deploy1
```