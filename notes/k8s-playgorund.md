# Kubernetes demo on Docker Playground

## Playground URL:
Login in `https://labs.play-with-k8s.com/` with your docker-id or github account.

## Initialize cluster
kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16 

## Setup POD network
kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml


## Allow Using master node for deployments
kubectl taint nodes --all node.kubernetes.io/not-ready:NoSchedule-
kubectl taint nodes --all node-role.kubernetes.io/master-

kubectl describe pods
