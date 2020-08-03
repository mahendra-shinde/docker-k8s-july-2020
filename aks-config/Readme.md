# Connect to AKS1200 Cluster

1. Open CMD/POWERSHELL and rename your existing ".kube\config" to ".\kube\config.old"

```
$ cd C:\Users\{USERNAME}\.kube
$ ren config config.old
```

2. Download the [config](./config) file into ".kube" folder.

    Click the [config](./config) and use "Raw" button to view file in RAW mode

    Use "Save" command (CTRL+S) to save this document in ".kube" folder.

3.  Test the cluster

```
$ kubectl get nodes
```