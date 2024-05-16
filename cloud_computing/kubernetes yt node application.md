 What will we do:
 create a node js application
 and we will configure the web server in such a way that it will respond with teh host name of the server when we connect to it using root url, like that we can distinguis which pod answers the requiest
- we will also dockerise and push to docker huib

then we create a deployment on this


krissal1234@pop-os:~/Documents/uni/kubernetes_notes$ k create deployment k8s-web-hello --image=krissal1234/k8s-web-hello

we create a cluster ip for this deployment
krissal1234@pop-os:~/Documents/uni/kubernetes_notes$ k expose deployment k8s-web-hello --port=3000

lets try connect to the cluster ip and port, so we connect to minikube node

minikube ssh
krissal1234@pop-os:~/Documents/uni/kubernetes_notes$ minikube ssh
                         _             

$ curl 10.105.81.168:3000
Hello from the k8s-web-hello-7f94b597dd-7qvxg$ 

k scale deployment k8s-web-hello --replicas=4

then inside the node if we spam the curl command we get responses from different nodes, so load balancing is woking
$ curl 10.105.81.168:3000 
Hello from the k8s-web-hello-7f94b597dd-6x9gw$ 
curl 10.105.81.168:3000
Hello from the k8s-web-hello-7f94b597dd-6x9gw$
curl 10.105.81.168:3000
Hello from the k8s-web-hello-7f94b597dd-7qvxg$ 
curl 10.105.81.168:3000
Hello from the k8s-web-hello-7f94b597dd-7qvxg$ 
curl 10.105.81.168:3000
Hello from the k8s-web-hello-7f94b597dd-pgng7$ 


we delete the service
k delete service k8s-web-hello

then we create another of type nodeport
krissal1234@pop-os:~/Documents/uni/kubernetes_notes$ k expose deployment k8s-web-hello --type=NodePort --port=3000
service/k8s-web-hello exposed

by setting it to node port we can now grap the ip of minikube using the new port of the service and connect to it

krissal1234@pop-os:~/Documents/uni/kubernetes_notes$ k get svc
NAME            TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
k8s-web-hello   NodePort    10.109.5.214   <none>        3000:32407/TCP   71s
kubernetes      ClusterIP   10.96.0.1      <none>        443/TCP          4h35m


krissal1234@pop-os:~/Documents/uni/kubernetes_notes$ curl 192.168.59.100:32407
Hello from the k8s-web-hello-7f94b597dd-7qvxg

NodePort service type exposes the port

