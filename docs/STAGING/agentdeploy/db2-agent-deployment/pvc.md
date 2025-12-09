# Configuring the `pvc.storageClass` variable

Scrolling to the end of the **db2z-agent** section of `values.yaml`, you should see the `pvc` section as shown below:
```
pvc:
  storageClass: "ocs-storagecluster-cephfs"
```

**Set the value of the `storageClass` variable** to your cluster's storage class: `managed-nfs-storage`.

After doing so, the result should look like the following:

```
pvc:
  storageClass: "managed-nfs-storage"
```