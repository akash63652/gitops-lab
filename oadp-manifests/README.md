# OADP Manifests (`openshift-adp` / `oadp-minio-1`)

## Apply with `oc`
- Create backup: `oc apply -f backup.yaml`
- Create daily schedule: `oc apply -f schedule.yaml`
- Restore backup: `oc create -f restore.yaml`
- Permanently delete backup (cluster + MinIO): `oc create -f delete-backup.yaml`

## Status Checks
```bash
oc -n openshift-adp get backup,schedule,restore,podvolumebackup
```

## Equivalent `oc oadp` CLI Commands
```bash
oc oadp backup create nextcloud-backup-manual --include-namespaces nextcloud --default-volumes-to-fs-backup --storage-location oadp-minio-1 --ttl 720h0m0s
oc oadp backup get
oc oadp backup describe nextcloud-backup-manual --details
oc oadp backup delete nextcloud-backup-manual --confirm
```
