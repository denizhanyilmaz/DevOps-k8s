# DevOps-k8s
## Install Kubernates Cluster
### Requirements
Install Vagrant and VirtualBox

### Clone Vagrant Script and Create Cluster
```
git clone https://github.com/scriptcamp/vagrant-kubeadm-kubernetes.git
cd vagrant-kubeadm-kubernetes
vagrant up
```

### Connect to master node:
`vagrant ssh master`

### Check the cluster:
`kubectl get node`

```
NAME            STATUS   ROLES                  AGE   VERSION
master-node     Ready    control-plane,master   78m   v1.23.0
worker-node01   Ready    worker                 71m   v1.23.0
worker-node02   Ready    worker                 65m   v1.23.0
```

## Install Jenkins on the Kubernetes Cluster

`kubectl create namespace jenkins`

`kubectl create -f jenkins.yaml -n jenkins`

`kubectl create -f jenkins-service.yaml -n jenkins`

`kubectl get svc -n jenkins`

```
NAME           TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
jenkins        NodePort    10.105.33.169    <none>        8000:30000/TCP   56m
jenkins-jnlp   ClusterIP   10.102.211.173   <none>        50000/TCP        56m
```

## Install Nexus on the Kubernetes Cluster

`kubectl create namespace nexus`

`kubectl create -f nexus.yaml -n jenkins`

`kubectl create -f nexus-service.yaml -n jenkins`

`kubectl get svc -n nexus`

```
NAME            TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
nexus-service   NodePort   10.98.246.75   <none>        8081:32000/TCP   37m
```
