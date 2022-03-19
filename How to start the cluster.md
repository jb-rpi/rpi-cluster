# How to launch the cluster on Master/Worker1 and Worker2 (3 RPIs)

## Pre-requisites:
Master has 10.0.0.50
Worker1  has 10.0.0.51
Worker2 has 10.0.0.52

The 3 nodes are on a LAN behind a rapsberry acting as wifi-router.

# Master:

$sudo kubeadm init --pod-network-cidr=10.244.0.0/16

In case anything wrong, check:

>1/ $ sudo swapoff -a

> 2/ $ sudo rm -R .kube

> 3/ $ sudo kubeadm reset

If everything is fine, at the end of the output we have something like:

"Then you can join any number of worker nodes by running the following on each as root:

> kubeadm join 10.0.0.50:6443 --token 7p3ngy.wgdcbk901sy53o3a \
    --discovery-token-ca-cert-hash sha256:065ec32af1fd4743bcac89573088a84d5beb076d1b334e9a60ae8cc73ba6a397 "
    
## Flannel 
 Then use of Flannel:
 
> $ kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml


# Workers:
 
 This is the command to run on the 2 other nodes.
 
 ## Clean-up

> $ mkdir -p ~/.kube
 
> $ sudo cp /etc/kubernetes/admin.conf ~/.kube/config
 
> $ sudo chown $(id -u):$(id -g) $HOME/.kube/config
 
 
## Join the Master:
 
> $ sudo kubeadm join 10.0.0.50:6443 --token 7p3ngy.wgdcbk901sy53o3a \
    --discovery-token-ca-cert-hash sha256:065ec32af1fd4743bcac89573088a84d5beb076d1b334e9a60ae8cc73ba6a397 

In case of error, check

> 1/$sudo kubeadm reset

You can then control that everything is fine with "kubectl get nodes" on the master.

Output here:

NAME      STATUS   ROLES                  AGE     VERSION

master    Ready    control-plane,master   15m     v1.20.1

worker1   Ready    <none>                 7m51s   v1.20.1
    
worker2   Ready    <none>                 5m13s   v1.20.2
