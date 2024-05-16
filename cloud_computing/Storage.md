lets say we have a mysql db pod that our application uses,
if data is added to the db, by default when you restart the pod, all the data is lost, becuase k8 does not giv eyou data persistence out of the box



We need a storage that does not depend on the pod lifecycle

we dont know on which node the pod restarts, so storage must be availbale on all nodes

storage needs to survive even if the cluster crashes


Persistent volume, is a cluster resource like ram or cpu that is used to store data
- it is created frmo a yaml file, how much storage?

by creating persistent volumes we can define which storage backen we can use, e.g. nfs/googlecloud/etc..

depending on the storage 

persistent volumes are not namespaced so they are accessible to the whole cluster

who creates perstent volumes and hwen?
applications need to claim the persitent volume claims

pvc claims a volume with a storage size, access type, and then any storage that satisfies thiis criteria willbeused

you have to use the pvc in pods configuaion

