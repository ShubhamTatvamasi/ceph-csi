# ceph-csi

Add `ceph-csi` repo:
```bash
helm repo add ceph-csi https://ceph.github.io/csi-charts
```

### RBS

Install `ceph-csi-rbd`:
```bash
helm upgrade -i ceph-csi-rbd ceph-csi/ceph-csi-rbd \
  --namespace ceph-csi \
  --create-namespace \
  --set "csiConfig[0].clusterID=47276ef5-9c84-4d2e-9972-27e533e00e0c" \
  --set "csiConfig[0].monitors[0]=10.43.171.152:6789" \
  --set "csiConfig[0].monitors[1]=10.43.49.201:6789" \
  --set "csiConfig[0].monitors[2]=10.43.155.148:6789" \
  --set secret.create=true \
  --set secret.userID="csi-rbd" \
  --set secret.userKey="AgC8JKdqRG0tECAAVh9qDngxobVygcNFbRNVSn/wnP8UAzWLLQ3c+ew52AY=" \
  --set storageClass.create=true \
  --set storageClass.clusterID="47276ef5-9c84-4d2e-9972-27e533e00e0c" \
  --set-string storageClass.annotations."storageclass\.kubernetes\.io/is-default-class"=true
```

### CephFS

Install `ceph-csi-cephfs`:
```bash
helm upgrade -i ceph-csi-cephfs ceph-csi/ceph-csi-cephfs \
  --namespace ceph-csi \
  --create-namespace
```
