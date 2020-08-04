## Pods

* Pods are Atomic Units
* Pods can have multiple (co-located) containers.
* Pods get IP Address and all container inside pod share the same
* Containers inside PODS must not listen on same port
* Containers inside POD can communicate with each other on "localhost"
* PODS are USUALLY part of
    - ReplicaSet
    - StatefulSet
    - Deployment
    - CronJobs
    - DaemonSet
* A Pod which is NOT Part of any other API Object is called static pod
* Static Pods do not benefit from SCALING or SELF HEALING

## Commonly Used commands on PODs

1. kubectl delete pod <PODNAME>
2. kubectl get pods
3. kubectl describe pod <PODNAME> # Get Deployment logs of POD with all other details
4. kubectl apply -f <filename>
5. kubectl exec -it <PODNAME> -c <CONTAINERNAME> <CMD-TO-EXEC>
6. kubectl logs -p <PODNAME> -c <CONTAINERNAME> # Application logs from Container inside the pod
