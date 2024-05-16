It is a container orchestration system
- using docker you can create multiple containers on one system, however if you want to create multiple containers on different servers, there will be some trouble
- you just tell kubernetes how many containers you want to create based on specific image


Kubernetes is shortened to k8s]

k8s takes care of the 
- automatic deployment of the containerised applications across different servers
- distribution of the load across multiple servers, allows resource management
- auto scaling of the deployed applications
- monitoring and health check of the containers
- replacement of the failed containers
All of this is done automatically

K8s deploys containerised applications, therefore it must use a specific container run time
- docker is one of them
- CRI-O is another


Terminology and Architecture

Pod is the smallest unit in the kubernetes world

![[Pasted image 20240509163143.png|400]]
- inside a pod you can have one or several containers
- shared volumes
- shared ip address
This means that all containers inside of the same pod share volumes and ip addresses
- This must be kept in mind when you want to have multiple containers in a pod
- All communication between these containers happens through localhost, as they are all part
of the same (Linux) namespace.


- One container per pod is the most common use case
	- Also each pod must be located on the same server, it is not possible to spread containers from one pod across different servers


Kubernetes cluster
- It consists of nodes, these could be baremetal or virtual servers, you could include multiple such servers in the kubernetes cluster. Usually nodes which belong to the same k8s cluster are located next to each other to be more efficient

Inside nodes are pods,
inside pods are containers
![[Pasted image 20240509163534.png|500]]
K8s does this job for you, but the developers job is to create such nodes and create cluster based on those nodes. Nodes will not automatically create clusters without developer intervention

How do nodes communicate with each other?
-  In a cluster there is a master node
	- the master node manages the worker nodes, and its the masters job to distribute load across other worker nodes. All pods related to your application runs on worker nodes
	- master node runs only system pods, which are resopnsible for actual work of the kubernets cluster in general
	- the master node could also be called the control plane and iit does not run your client applications

![[Pasted image 20240509163910.png|400]]

Kubernetes services

**kubelet, kube-proxy and container runtime** are present in each node in a k8s cluster

- container run time runs containers in each node, e.g. docker
- kubelet, this service exists on each worker node that communicates with the api server in the master node. the API server is the main point of communications between nodes in the kubernetes world
- Kube-proxy, which is present on each node is responsible for network communication inside each node and other nodes

The master node has
- Scheduler:  such service is responsible for planning distribution of the load on different nodes in the cluster
- kube controller manager: controls what happens on each of the nodes in the cluster
- cloud controller manager: its job is in relation with cloud service provider, where you run teh kubernetes cluster, as you usually run kubernetes cluster on a cloud provider rather than your own servers. For that you have to run the cloud controller manager service on the master node
- etcd: This is a service which actually stores all logs related to the operation of the k8s cluster stored as key value pairs

other services could include dns, which would allow for names resolution in the entire cluster, for instance yoyu can connect to a specific deployment through a name
![[Pasted image 20240509164613.png]]

the main service on teh master node is the api server

Cluster management
- kubectl is a seperate cli tool that allows you to connect to a k8s cluster and manage it remotely
- using such a tool you connect using REST HTTPS
- other nodes communicate with the master node in teh same fashion

![[Pasted image 20240509164915.png|600]]

minikub is a software that allows you to run a cluster locally, 
- it essentially create a single node cluster that acts as worker node and master node

to run minkube you need a VM or container manager



minkube start to create cluster
--driver "" to specify which driver, e.g. docker, virtualbox etc..
to find out which ip address was assigned to the node
krissal1234@pop-os:~$ minikube ip
192.168.59.100

now we can ssh into it
![[Pasted image 20240509171651.png]]
![[Pasted image 20240509171741.png]]



or you can use minikube ssh to get in

once inside we can run docker ps to check the containers
- we can see contains for kube api server, schedule, as mentioned before

kubectl is an external tool manage the cluster so we dont have it in the cluster
- command is not found if attemtped to use it within the minkube cluster



krissal1234@pop-os:~$ kubectl cluster-info
Kubernetes control plane is running at https://192.168.59.100:8443
CoreDNS is running at https://192.168.59.100:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy


krissal1234@pop-os:~$ kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   17m   v1.30.0


krissal1234@pop-os:~$ kubectl get pods
No resources found in default namespace.

**lets list all namespaces**
krissal1234@pop-os:~$ kubectl get namespaces
NAME              STATUS   AGE
default           Active   17m
kube-node-lease   Active   17m
kube-public       Active   17m
kube-system       Active   17m

- Namespaces are used to group different configurations and objects
- if you list get pods, you get the pods in the default namespace

there is a name space option to see pods in another e.g:
krissal1234@pop-os:~$ kubectl get pods --namespace=kube-system
NAME                               READY   STATUS    RESTARTS      AGE
coredns-7db6d8ff4d-9mrjr           1/1     Running   0             18m
etcd-minikube                      1/1     Running   0             18m
kube-apiserver-minikube            1/1     Running   0             18m
kube-controller-manager-minikube   1/1     Running   0             18m
kube-proxy-dvbmf                   1/1     Running   0             18m
kube-scheduler-minikube            1/1     Running   0             18m
storage-provisioner                1/1     Running   1 (18m ago)   18m


Lets create a pod manually

--image=nginx is the docker image
krissal1234@pop-os:~$ kubectl run nginx --image=nginx
pod/nginx created


**We can describe a pod to get information on i**t
krissal1234@pop-os:~$ kubectl describe pod nginx 

to connect to pods we have to create services we cannot simply use its ip



there are always pause containers, in order to lock namespace

we can enter a container, by going into the minkube cluster, and doing docker exec -it "id of container found in docker ps -a"
then 


kubectl get pod [pod-name] -o yaml
to get yaml

minikube ssh

to delete pod
kubectl delete pod nginx


most common way to create multiple pods where you can increasee quantity and modify  is using deployments
- kubectl create deployment nginx-deployment --image=nginx

kubectl get deployments


selectors in describe are used to connect pods with deployments, becuase they are separate objects

replica field: quantity of the pods which are desired, updated , total and avaliable

strategy type: shows how to perform updates of deployments

If there are multiple pods in the same deployment which belong to the same replica set you'll see sane prefix in "get pods" but same hash (last number)

- Now there was deployment, inside of deployment is replica set( replicas of pods in case one fails) 
	- and pods are managed by this deployment


Now lets scale the deployment and injcrease quantity of the pods in teh deployment
kubectl scale deployment nginx-deployment --replicas=5

we just scaled our deployment into 5 different replicas and now there are 5 pods running#nginx-deployment-c45d79c8-5bvxr   1/1     Running   0          11s
nginx-deployment-c45d79c8-cgd7p   1/1     Running   0          11m
nginx-deployment-c45d79c8-fxhv4   1/1     Running   0          11s
nginx-deployment-c45d79c8-j8hz8   1/1     Running   0          11s
nginx-deployment-c45d79c8-pmhvt  

each pod has different ip address, by doing: k get pods -o wide

- each pod has the same name but the hashes are different

lets try to connect to one of the pods
- minikube ssh
- curl 10.244.0.6
we are getting response when we connect to the pods within the node, enabling me to connect to the pods inside

You should not rely on the ip addresses of the pods if you would like to connect to a specific pod. We need to utilise another ip address that allows you to connect externally. This is done through services
- ClusterIP - this will create a single external ip address with a load balancer

we already have a deployment created
ent_2/task_2$ k get deployments
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   3/3     3            3           28m


now lets create a service, for this deployment, with this service we can expose a specific port from the deployment

we have to expose internal port 80 (nginx port) into any other port outside of the deployment, e.g. 8080
to expose we do:
krissal1234@pop-task_2$ k expose deployment nginx-deployment --port=8080 --target-port=80
service/nginx-deployment exposed

Now we can get services:
k get services:
- the ip address found here is completely different to the ip addresses assigned to the pods, this is a virtual ip address created by kubernetes, which could be used to connect to any of the pods
- Cluster ip will only be avajlable inside of the cluster
ent_2/task_2$ k get services
NAME                        TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
kubernetes                  ClusterIP   10.96.0.1        <none>        443/TCP    3h19m
my-postgres-postgresql      ClusterIP   10.104.199.114   <none>        5432/TCP   48m
my-postgres-postgresql-hl   ClusterIP   None             <none>        5432/TCP   48m
nginx-deployment            ClusterIP   10.100.136.61    <none>        8080/TCP   17s

clusterIP is not available outside the cluster, so i cannot connect to 
curl 10.100.136.61:8080 from my pc
however we are able to access the ip from any node
e.g.:
minikube ssh
curl 10.100.136.61:8080



lets describe the service
k describe service nginx-deployment
ent_2/task_2$ k describe service nginx-deployment
Name:              nginx-deployment
Namespace:         default
Labels:            app=nginx-deployment
Annotations:       <none>
Selector:          app=nginx-deployment
Type:              ClusterIP
IP Family Policy:  SingleStack
IP Families:       IPv4
IP:                10.100.136.61
IPs:               10.100.136.61
Port:              <unset>  8080/TCP
TargetPort:        80/TCP
Endpoints:         10.244.0.11:80,10.244.0.6:80,10.244.0.8:80
Session Affinity:  None
Events:            <none>

- we get three endpoints, these endpoints indicate particular ports, load 
-will be balanced on these endpoints


Now we know how to create a pod, how to create deployment, how to scale deployment and how to create a service for the deployment



In Kubernetes, a Deployment is a higher-level concept that manages the deployment and scaling of a set of Pods, and allows for declarative updates to those Pods along with their configurations. It is built on top of the ReplicaSet to provide additional features such as rolling updates and rollbacks, making it a fundamental construct for managing containerized applications within a Kubernetes cluster.
Core Functions of a Deployment

    Managing ReplicaSets: A Deployment automatically manages ReplicaSets, which in turn manage the Pods. Unlike directly using ReplicaSets, a Deployment can handle the lifecycle of several ReplicaSets, orchestrating updates and rollbacks.

    Scaling: A Deployment can be easily scaled up or down by simply adjusting the number of replicas specified in the deployment configuration. This scaling adjusts the ReplicaSets and, by extension, the Pods.

    Updating and Rolling Updates: When you update the configuration of a Deployment, such as changing the container image, Kubernetes will gradually update the Pods in a controlled way. This is known as a rolling update. Rolling updates allow Deployment updates to be rolled out without downtime by incrementally updating Pods instances with new ones.

    Rollbacks: If something goes wrong, Kubernetes Deployments allow you to easily rollback to a previous version of your Deployment which makes them very valuable for Continuous Deployment practices.

    Self-healing: Deployments automatically replace Pods that fail, are deleted, or are terminated. By using a Deployment, you ensure that a specified number of Pods are always running, even in the event of failure.







declerative approach requires creating deployment.yaml 

lets apply it
$ kubectl apply -f deployment.yaml 
deployment.apps/k8s-web-hello created

we can apply a service.yaml too
krissal1234@pop-os:~/Documents/uni/kubernetes_notes/k8s$ kubectl apply -f service.yaml
service/k8s-web-hello created



