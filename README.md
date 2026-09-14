# ceph-csi

Add `ceph-csi` repo:
```bash
helm repo add ceph-csi https://ceph.github.io/csi-charts
```

### RBD

Install `ceph-csi-rbd`:
```bash
helm upgrade -i ceph-csi-rbd ceph-csi/ceph-csi-rbd \
  --namespace ceph-csi-rbd \
  --create-namespace \
  --set "csiConfig[0].clusterID=dc176f2a-a507-11f1-a340-bc241144dae3" \
  --set "csiConfig[0].monitors[0]=10.10.153.255:6789" \
  --set "csiConfig[0].monitors[1]=10.10.169.182:6789" \
  --set "csiConfig[0].monitors[2]=10.10.204.94:6789" \
  --set provisioner.replicaCount=1 \
  --set secret.create=true \
  --set secret.userID="csi-rbd" \
  --set secret.userKey="AgBVdadqSar3CCAAW9dRV9YxWdZSn3aeGtqI8zlOWgZuR5j1IJL02eNg8bY=" \
  --set storageClass.create=true \
  --set storageClass.pool=kubernetes \
  --set storageClass.clusterID=dc176f2a-a507-11f1-a340-bc241144dae3 \
  --set-string storageClass.annotations."storageclass\.kubernetes\.io/is-default-class"=true
```

### CephFS

Install `ceph-csi-cephfs`:
```bash
helm upgrade -i ceph-csi-cephfs ceph-csi/ceph-csi-cephfs \
  --namespace ceph-csi-cephfs \
  --create-namespace \
  --set "csiConfig[0].clusterID=dc176f2a-a507-11f1-a340-bc241144dae3" \
  --set "csiConfig[0].monitors[0]=10.10.153.255:6789" \
  --set "csiConfig[0].monitors[1]=10.10.169.182:6789" \
  --set "csiConfig[0].monitors[2]=10.10.204.94:6789" \
  --set provisioner.replicaCount=1 \
  --set secret.create=true \
  --set secret.userID=k8s-cephfs \
  --set secret.userKey="AgC/e6dqvlN5CiAAwBog3UUgg0RuGkEX1R3k28T/NatvSi/x1tLj5XjFMQU=" \
  --set storageClass.create=true \
  --set storageClass.fsName=k8s-cephfs \
  --set storageClass.clusterID=dc176f2a-a507-11f1-a340-bc241144dae3
```
