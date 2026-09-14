# Test PVC

Create postgres with `csi-rbd-sc` Storage Class:
```bash
helm upgrade -i postgres \
  oci://registry-1.docker.io/cloudpirates/postgres \
  --set auth.password="postgres" \
  --set persistence.storageClass=csi-rbd-sc
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
