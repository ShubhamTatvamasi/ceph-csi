# CephFS

Create a new `k8s-cephfs` pool:
```bash
ceph fs volume create k8s-cephfs
```

Create a user:
```
ceph auth get-or-create client.k8s-cephfs \
  mon 'allow r' \
  mgr 'allow rw' \
  mds 'allow rw' \
  osd 'allow rw tag cephfs *=*'
```
