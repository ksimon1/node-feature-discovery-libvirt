# NFD Libvirt
**NFD Libvirt** is a feature which runs [node-feature-discovery](https://github.com/kubernetes-incubator/node-feature-discovery) and [libvirt](https://github.com/kubevirt/libvirt) containers
in the same pod. Libvirt container runs `virsh domcapabilities --machine q35 --arch x86_64 --virttype kvm` command and output saves into `/usr/share/virsh/virsh-domcapabilities.xml` file. Folder `/usr/share/virsh` is shared between NFD and libvirt container.

**Usage:**
```
kubectl create -f node-feature-discovery-libvirt-daemonset.yaml.template

kubectl exec -it <pod name> --container node-feature-discovery -- cat /usr/share/virsh/virsh-capabilities
```

**Future plans:**
Parse libvirt output and integrate it into NFD - [nfd-host-supported-cpus](https://github.com/ksimon1/nfd-host-supported-cpus)
