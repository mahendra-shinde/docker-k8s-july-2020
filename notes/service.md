## Services

* Base service type is `ClusterIP`
* ClusterIP Services are INTERNAL services, not accessible from Outside cluster
* ClusterIP Services have both IP and DNS name

* NodePort Services exposed on a SPECIAL port mapped to ALL Nodes in Kubernetes.
* An External User/Client should use `NODE-ip:Node-port` to access your service.
* An Internal User/Client should use `cluster-ip:service-port` to access your service.
* For a Nodeport service, you MUST share Node-IP with External Client
* You can create a seperate Load Balancer and Connect your NodePort service to LB.

* LoadBalancer Service: a feature implemented by Cloud Vendors
* Your Vendor, would actually create NodePort service.
* Then, it would create a LOAD BALANCER with PublicIP and Map it to NodePort service.
* An Internal User/Client can use all three options to connect service
    - node-ip:node-port
    - cluster-ip:service-port
    - external-ip:service-port
