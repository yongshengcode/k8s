
https://github.com/kubernetes-csi

### CSI Hostpath Driver

not working


### NFS CSI driver
https://github.com/kubernetes-csi/csi-driver-nfs/blob/master/docs/install-csi-driver-master.md

- Set up a NFS Server on a Kubernetes cluster
https://github.com/kubernetes-csi/csi-driver-nfs/blob/master/deploy/example/nfs-provisioner/README.md

```
# NFS Server节点安装部署
apt-get update;apt-get -y install nfs-kernel-server
mkdir /storage && echo "/storage *(rw,sync,no_root_squash)" >> /etc/exports
systemctl restart nfs-kernel-server

# NFS Client节点安装部署
apt-get -y install nfs-common
```



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
