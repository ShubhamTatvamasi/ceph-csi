# CephFS

Create a new `kubernetes-cephfs` pool:
```bash
ceph osd pool create k8s-cephfs-data
ceph osd pool create k8s-cephfs-metadata
```

For CephFS, enable the appropriate application:
```bash
ceph osd pool application enable k8s-cephfs-data cephfs
ceph osd pool application enable k8s-cephfs-metadata cephfs
```

Create the CephFS
```bash
ceph fs new k8s-cephfs \
  k8s-cephfs-metadata \
  k8s-cephfs-data
```

Create a user:
```
ceph auth get-or-create client.k8s-cephfs \
  mon 'allow r' \
  mgr 'allow rw' \
  mds 'allow rw' \
  osd 'allow rw tag cephfs *=*'
```
