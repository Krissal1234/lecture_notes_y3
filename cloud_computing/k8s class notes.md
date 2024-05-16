
Pod-level networking
– Pod-to-Pod communication happens using Pod IPs, whether you deploy the Pod on the same
node or a different node in the cluster
– A virtual (software) network bridge connects virtual net interfaces created for each pod on the
same host node
– Using Pod IPs however is not compatible with the dynamic nature of Pod IPs, stemming from
replication and scheduling on multiple nodes inside the cluster

![[Pasted image 20240509175939.png]]
### Container-to-Container & Pod-to-Pod Networking

The diagram at the top shows how containers within Kubernetes pods communicate with each other across different nodes using a virtual network bridge:

1. **Pod Network Namespace**: Each pod in Kubernetes has its own network namespace. This provides isolation and allows each pod to have its own IP address and routing table.
    
2. **Containers in a Pod**: Containers within the same pod can communicate with each other via `localhost`, as they share the same network namespace. For example, Container 1 can send network traffic to Container 2 without leaving the pod.
    
3. **Virtual Bridge**: Pods on different nodes communicate through a virtual network bridge. This bridge routes the traffic between pods across nodes, using virtual ethernet devices (`veth` pairs).
    
4. **Root Network Namespace**: This represents the main network namespace of the host node, which has its own interfaces and routing rules to facilitate communication between pods across different nodes.
    

### ClusterIP Services

The text below the diagram explains how ClusterIP services work in Kubernetes:

- **Stable Virtual IPs**: ClusterIP services provide a stable IP address (known as a Virtual IP or VIP) that remains constant even as backend pods are added, removed, or changed. This IP doesn't route directly to a single pod; instead, it serves as an entry point for accessing the services.
    
- **Routing & Load Balancing**: Traffic to a ClusterIP is managed by `kube-proxy`, which uses IP tables or IP Virtual Server (IPVS) to route requests to the appropriate pods. `kube-proxy` can load balance traffic across multiple pods using either round-robin or random selection.
    
- **DNS Mapping**: In Kubernetes, service names are mapped to virtual IPs by the cluster DNS server. This allows applications to refer to services by name rather than IP address, making configurations easier and more maintainable.
    
- **Service YAML Definition**: The example YAML configuration shows how a Kubernetes service is defined. This particular example defines a service named `nginx-service` which targets pods with the label `app: nginx`. The service routes traffic on port 80 to the `targetPort` (also port 80) on the backend pods. This abstraction allows Kubernetes to handle the complexity of routing client requests to the correct pod instances.
- ![[Pasted image 20240509180443.png|400]]
 ![[Pasted image 20240509180259.png|600]]

![[Pasted image 20240509180717.png]]

The slide in your presentation notes explores how Kubernetes services, particularly NodePort and LoadBalancer types, allow pods to be exposed externally, facilitating access outside the cluster. Let's break down the details:

### NodePort

- **Purpose**: This type of service makes a pod accessible from outside the Kubernetes cluster by adding a specific port (NodePort) to each node in the cluster. This port forwards traffic to the appropriate pod, either directly or via `kube-proxy`, which handles the traffic routing using iptables or IPVS.
    
- **Configuration**: As shown in the YAML example, a NodePort service has:
    
    - `type: NodePort`: Specifies the service type.
    - `ports`: A list of ports to expose on the cluster nodes, where:
        - `port`: The port that will be exposed on the service itself inside the cluster.
        - `targetPort`: The port on the pod that the service should forward to.
        - `nodePort`: The specific port allocated on all nodes that will route to the `targetPort`. This port is open on every node’s IP at a specific port number specified (32023 in the example).

### LoadBalancer

- **Purpose**: This service extends the functionality of NodePort by integrating with cloud providers' load balancers to distribute incoming traffic among pods. This setup provides a single point of access to the service via a stable, public-facing IP address, which is managed by the cloud provider.
    
- **Characteristics**:
    
    - Typically provided by cloud environments (like AWS, Azure, GCP).
    - More expensive than other service types due to the use of cloud resources.
    - Automatically assigns a public IP address.
    - Can be configured to work with Ingress resources to handle routing to multiple services from a single IP address based on the URL path.

### Diagram Explanation

- The diagram illustrates the flow of external traffic into the Kubernetes cluster:
    - **External Requests**: Originating from the internet, these are directed to either a NodePort or a LoadBalancer IP.
    - **LoadBalancer / NodePort**: These components route the incoming traffic to the appropriate node and port on that node.
    - **kube-proxy & iptables/IPVS**: These elements on each node handle the final routing of traffic to the correct pod within the node, based on the service configuration.

### Summary

This setup allows Kubernetes to expose services in a controlled and scalable manner, providing robust options for handling incoming traffic, load balancing, and fault tolerance. NodePort is simpler and generally used for development or smaller environments, whereas LoadBalancer is suited for production environments requiring high availability and scalability.





![[Pasted image 20240509182211.png]]
This slide provides an overview of how Kubernetes handles storage, specifically focusing on concepts like Persistent Volumes (PVs), Persistent Volume Claims (PVCs), and VolumeMounts. Let's break down each of these concepts:

### Persistent Volume (PV)

- **Purpose**: A Persistent Volume (PV) in Kubernetes is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using StorageClasses. It is a resource in the cluster just like a node is a cluster resource.
- **Characteristics**:
    - **Immutable Containers**: Since containers are designed to be ephemeral and immutable, any persistent data needs to be stored outside of the containers themselves. PVs provide a method for this external storage.
    - **Provisioning**: PVs can be provisioned statically (pre-provisioned storage) or dynamically. Static provisioning involves the administrator creating a PV that is available for use. Dynamic provisioning uses a StorageClass to automatically create the storage when it is requested by users.
    - **StatefulSets**: When using StatefulSets, PVs are not deleted when the StatefulSet is deleted, ensuring that the data persists and can be reused.

### Persistent Volume Claim (PVC)

- **Purpose**: A Persistent Volume Claim is a request for storage by a user. It specifies size, and access modes like read/write, once or many times.
- **Dynamic Provisioning**: PVCs typically use StorageClasses to dynamically provision the required storage. A StorageClass defines the type of storage used (such as SSDs or slower disks) and provisions storage from the underlying infrastructure (like AWS EBS, Google PD, etc.).
- **VolumeClaimTemplates**: Within StatefulSets, PVCs are defined using templates that allow each instance in the set to have its own persistent storage, adhering to the defined template.

### VolumeMount

- **Purpose**: This component of a pod’s spec specifies exactly how the volumes (either PVs or ephemeral volumes) are mounted into pods.
- **Details**:
    - **Mount Path**: The location within the container where the volume should be mounted.
    - **Volume Types**: Volume mounts can handle both ephemeral (temporary data tied to the pod lifecycle) and persistent storage, making them versatile for different application needs.

### Diagram and Flow

- **Provisioning Flow**: The diagram likely illustrates how storage requests are fulfilled. A PVC requests a certain type of storage, which is provisioned and then mounted into the containers as volumes. The flow from a storage request to the actual mounting inside a pod demonstrates how Kubernetes abstracts the complexity of handling storage, allowing developers to focus on the application logic rather than the specifics of the storage infrastructure.

Overall, this slide emphasizes Kubernetes' ability to manage complex storage needs in a dynamic and scalable environment, allowing applications running within the cluster to have stable and reliable access to the data they need to perform their functions.