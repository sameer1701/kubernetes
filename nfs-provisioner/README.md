# NFS auto provisioner

### Pre-requisites 
- Install nfs-server
- Configure <b>/etc/exports</b></br>
 <code>     /srv/nfs/kubedata *(rw,sync,no_root_squash) </code>
- Restart nfs server 
- Install nfs client on all the nodes
### Steps
<code>
 - kubectl apply -f class.yaml rbac.yaml deployment.yaml
</code>

### The Helm way
Run below helm commands to deploy nfs provisioner by helm</br>

<code>helm repo add nfs-subdir-external-provisioner https://kubernetes-sigs.github.io/nfs-subdir-external-provisioner/ </code></br>
<code>helm install nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner --set nfs.server=192.168.56.2 --set nfs.path=/srv/nfs/kubedata/</code>