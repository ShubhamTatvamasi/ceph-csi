# Test PVC

Create postgres with `ceph-csi-rbd` Storage Class:
```bash
helm upgrade -i postgres \
  oci://registry-1.docker.io/cloudpirates/postgres \
  --set auth.password="postgres" \
  --set persistence.storageClass=ceph-csi-rbd
```

Create postgres with `csi-cephfs-sc` Storage Class:
```bash
helm upgrade -i postgres \
  oci://registry-1.docker.io/cloudpirates/postgres \
  --set auth.password="postgres" \
  --set persistence.storageClass=csi-cephfs-sc \
  --set "persistence.accessModes[0]=ReadWriteMany"
```

Test Postgres:
```bash
kubectl exec postgres-0 -- psql -c '\l'
```
