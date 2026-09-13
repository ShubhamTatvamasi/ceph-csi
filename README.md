# ceph-csi

Add `ceph-csi` repo:
```bash
helm repo add ceph-csi https://ceph.github.io/csi-charts
```

Install `ceph-csi-rbd`:
```bash
helm install ceph-csi-rbd ceph-csi/ceph-csi-rbd \
  --namespace ceph-csi \
  --create-namespace
```

Install `ceph-csi-cephfs`:
```bash
helm install ceph-csi-cephfs ceph-csi/ceph-csi-cephfs \
  --namespace ceph-csi \
  --create-namespace
```
