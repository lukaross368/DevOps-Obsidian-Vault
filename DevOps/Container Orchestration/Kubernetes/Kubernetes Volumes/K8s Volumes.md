#devops #containers #k8s #dataBases #k8sAdmin

Volumes can be used to persist data in kubernetes.

Be default when pods (see  [[Main k8s Components]]) are restarted data is not persisted.

We therefore need a storage component that does not depend on the pod lifecycle. Other requirements are that It must be available from all nodes in the cluster and that it needs to survive even if the cluster crashes.

### Persistent Volume

A persistent volume is a cluster resources created using a YAML file. 

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: example-pv
spec:
  capacity:
    storage: 5Gi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Recycle
  storageClassName: slow
  mountOptions:
	- hard
	- nfsvers=4.0
  nfs:
	path: /dir/path/on/nfs/server
	server: nfs-server-ip-address
```

But remember, Persistent Volume is just an abstract concept. We need actual storage like local hard drive or some cloud storage. Persistent Volume is just the Interface to an actual storage you maintain (back up, prevent corruption, etc. )

Persistent Volumes are not Namespaced (see [[K8s Namespaces]])

Persistent Volumes can Interface with two types of Storage, Local and Remote. However local volumes will violate 2 of the 3 requirements at the top of this page. They will be tied to a single node since they are a local storage,  and also surviving after a cluster crash as the node hosting the local storage will crash. For DB persistence you should almost always use Remote Storage.

Persistent Volume Must already exist in the cluster before we deploy pods across our cluster that depend on the storage. Therefore it is the job of the Cluster Administrator to make sure both the actual storage and the persistent volumes these are accessible when we go to deploy resources into our kubernetes Cluster.

### Persistent Volume Claim

Now we have our remote storage set up and our admin has created a namespace-independent Persistent Volume to interface with it,  we need to define a resource in our namespace that references the persistent volume in our cluster. These are also created with a YAML file. In the file we specify some details about the type of storage our application wants and whichever persistent storage in our cluster matches it will be used. 

```yaml
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: pvc-name
spec:
  storageClassName: manual
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
```

Then our Pod need to reference this persistent volume claim under the' volumes' part of the pod spec

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
    - name: myfrontend
      image: nginx
      volumeMounts:
      - mountPath: "/var/www/html"
        name: mypd
  volumes:
    - name: mypd
      persistentVolumeClaim:
        claimName: pvc-name
```



### Storage Class

What if we have a large cluster with lots of pods with a lot of different storage requirements. The Cluster Admin will have to be creating a lot of persistent volume resources so that the application pods can talk to the remote storages. Storage class solves this problem by automatically and dynamically provisioning persistent volumes in our cluster. 

Created with our YAML config files
```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: storage-class-name
provisioner: kubernetes.io/aws-ebs
parameters:
  type: io1
  iopsPerGB: "10"
  fsType: ext4
```

