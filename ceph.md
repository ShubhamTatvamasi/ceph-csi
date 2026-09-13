# ceph

Get Ceph cluster ID:
```bash
ceph fsid
```

Get Ceph Monitor Endpoints:
```bash
ceph mon dump
```

Create a new `kubernetes` pool:
```bash
ceph osd pool create kubernetes
```

Initalize `kubernetes` pool as RBD:
```bash
rbd pool init kubernetes
```

Create a new user for CSI:
```bash
ceph auth get-or-create client.csi-rbd \
  mon 'profile rbd' \
  osd 'profile rbd pool=kubernetes' \
  mgr 'profile rbd pool=kubernetes'
```

Get the details of client:
```bash
ceph auth get client.csi-rbd
```
