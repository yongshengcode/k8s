
https://github.com/kubernetes-csi

### CSI Hostpath Driver

not working


### NFS CSI driver
https://github.com/kubernetes-csi/csi-driver-nfs/blob/master/docs/install-csi-driver-master.md

 - Option#2. local install
```console
git clone https://github.com/kubernetes-csi/csi-driver-nfs.git
cd csi-driver-nfs
./deploy/install-driver.sh master local
```

- check pods status:
```console
kubectl -n kube-system get pod -o wide -l app=csi-nfs-controller
kubectl -n kube-system get pod -o wide -l app=csi-nfs-node
```

There was some network errors when i did install above plugins, and I updated the proxies for Docker to solve the network issue. Refer to https://github.com/yongshengcode/docker/blob/main/install.md
