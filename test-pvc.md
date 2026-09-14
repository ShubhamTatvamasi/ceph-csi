# Test PVC

Test `ceph-csi-rbd`: 
```
helm upgrade -i postgres \
  oci://registry-1.docker.io/cloudpirates/postgres \
  --set auth.password="postgres" \
  --set persistence.storageClass=ceph-csi-rbd
```

Test `csi-cephfs-sc`: 
```
helm upgrade -i postgres \
  oci://registry-1.docker.io/cloudpirates/postgres \
  --set auth.password="postgres" \
  --set persistence.storageClass=csi-cephfs-sc \
  --set "persistence.accessModes[0]=ReadWriteMany"
```
