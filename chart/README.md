# __NAME__

## Installation

```
    # Todo: Document any required values, if they exist.
    $ helm upgrade --install path/to/__NAME__ __NAME__
```

### Persistence

There are two storage APIs in Kubernetes that handle persistence abstraction:

- volume.alpha.kubernetes.io/storage-class
- volume.beta.kubernetes.io/storage-class

These APIs have different behaviours, across different cluster versions. The alpha API will be used if a storage class is not specified in the `storageClass` input, as it defers storage to to the cluster and the cluster will provision some based on its configured defaults. However, if the administrator needs to provision this storage (such as in the local development environment), they should set the `storageClass` attribute to match their configured storage, after which the beta API will be used.

An example PV might look something like the following:

```
  ---
  apiVersion: "v1"
  kind: "PersistentVolume"
  metadata:
    name: "foo-mysql"
    annotations:
      volume.beta.kubernetes.io/storage-class: "foo-mysql"
  spec:
    capacity:
      storage: "10Gi"
    accessModes:
      - "ReadWriteOnce"
    persistentVolumeReclaimPolicy: "Retain"
    hostPath:
      path: /mnt/mysql
```

### Existing PersistentVolumeClaims

1. Create the PersistentVolume
```bash
$ cat <<EOT | kubectl create -f -
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: test
  labels:
    volume_name: test
spec:
  capacity:
    storage: 2Gi
  accessModes:
    - ReadWriteOnce
  nfs:
    server: nfs.example.com
    path: "/test"
  persistentVolumeReclaimPolicy: Retain
EOT
```
1. Create the PersistentVolumeClaim
```bash
$ cat <<EOT | kubectl create -f -
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: test
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 2Gi
  selector:
    matchLabels:
      volume_name: test
EOT
```
1. Create the directory, on a worker
```bash
# mkdir -m 1777 /NFS_MOUNT/test
```
1. Install the chart
```bash
$ helm install --name test --set persistence.existingClaim=test .
```

## Usage

// Todo: Write up usage.
