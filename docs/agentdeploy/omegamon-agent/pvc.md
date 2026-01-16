# Configuring the `pvc.storageClass` variable

Scrolling to the end of the **omegamon-insights-agent** section of `values.yaml`, you should see the `pvc` section as shown below:
```
pvc:
  storageClass: "ocs-storagecluster-cephfs"
```

**Set the value of the `storageClass` variable** to your cluster's default storage class: `ocs-external-storagecluster-ceph-rbd`.

After doing so, the result should look like the following:

```
pvc:
  storageClass: "ocs-external-storagecluster-ceph-rbd"
```