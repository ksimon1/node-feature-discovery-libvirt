# NFD Libvirt
**NFD Libvirt** is a feature which runs [node-feature-discovery](https://github.com/kubernetes-incubator/node-feature-discovery) and [libvirt](https://github.com/kubevirt/libvirt) containers
in the same pod. Libvirt container runs `virsh capabilities` command and output saves into `/usr/share/virsh/virsh-capabilities` file. Folder `/usr/share/virsh/virsh-capabilities` is shared between NFD and libvirt container.

**Usage:**
```
kubectl create -f rbac.yaml

kubectl create -f node-feature-discovery-libvirt-daemonset.yaml.template

kubectl exec -it <pod name> --container node-feature-discovery -- cat /usr/share/virsh/virsh-capabilities
```

**Future plans:**
Parse libvirt output and integrate it into NFD.
