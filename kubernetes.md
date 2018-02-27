# Kubernetes notes

## Kubernetes

Head node

  - The "brain"
  - Runs the following services
    - API server
    - Scheduler - Place containers where they need to go
    - Controller manager - make sure state of system is good
    - Etcd - datastore for state
  - Runs the following processes
    - kubelet - process that reads yml files in `/etc/kubernetes/manifests/` and starts them
    - docker
  - Head node be one of the worker nodes also
  
Worker node

  - Runs the following processes
    - kubelet - agent that talks to API server and local docker daemon
    - docker
  - Provides kube-proxy - IP tables for each worker node

## Install Minikube

Install Hypervisor via virtualbox

```
brew tap phinze/homebrew-cask && brew install brew-cask-completion
brew cask install virtualbox
```

Install kubectl

```
brew install kubectl
```

Install minikube

```
curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.25.0/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```

Use minikube

Start a VM in virtualbox called minikube, and run a process called localkube, which runs API server, Scheduler, Controller manager. Also runs docker in that vm

```
minikube start
minikube status
minikube stop
```

View kube version in client and server

```
kubectl version
```

Get list of nodes in cluster

```
kubectl get nodes
```

See docker containers running inside minikube

```
# Connect to minikube terminal
minikube ssh

docker ps
exit
```

Open minikube dashboard in browser

```
minikube dashboard
```


## Manually setup kubernetes cluster using kubeadm

Download kubeadm and its dependencies in the head node as well as all the worker nodes

Setup admin node - downloads docker containers for scheduler, controller, api server, etc

```
kubeadm init
```

When this command finishes, run the 3 lines of commands printed near the bottom
Also, in the worker nodes, run the single line command at the bottom

Restart kubelet in all the worker nodes (and head node, since it's also a worker)

```
systemctl restart kubelet
```

In the head node, check to make sure that the worker nodes have been added

```
kubectl get nodes
```

This will show all the nodes' status as NotReady because the network hasn't been set up

Install pod network, i.e. Weave Net by running provided command in master node

Running the command above should show all status Ready


## Use Kubernetes through accessing the Kubernetes API

`kubectl` is cmd line client to interact with kubernetes API server

```
# View list of resources
kubectl get <resource>
kubectl get pods
kubectl get deployments

# Create a deployment using image from docker hub
kubectl run ghost --image=ghost

# Verbose mode to see web service endpoint url
kubectl -v=9 get pods

# Describe pod
kubectl describe pod <NAME>

# Get config yaml
kubectl get deployment/hello-flask -o yaml

# Delete a deployment
kubectl delete deployment ghost
```

Need to use proxy to talk to kube API server

```
# Start proxy so that we don't have to deal with TLS, authentication, etc
kubectl proxy

# Same as kubectl get pods
curl http:://localhost:8001/api/v1/namespaces/default/pods
```
