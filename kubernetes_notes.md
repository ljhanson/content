Title: Kubernetes Notes
Date: 9/13/2019 10:16 PM
Author: L.J. Hanson
Tags: docker, kubernetes, linux, 
Slug: 
Your Kubernetes control-plane has initialized successfully!
```bash
* Kubeadm init to start the cluster off.
```

Success:
```bash
To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 192.168.1.160:6443 --token bt5jqu.92na40x473dukgdb \
    --discovery-token-ca-cert-hash sha256:2c2962c2f31519a5946064a1bbc0671367d4dd9630715ecfb2c71dfd1d4eed28
```
Other notes:
* Swap must be turned off (Caught in kubeadm preflight)
* Selinux must be off and disabled
* Ports:
![Network Ports](https://i.stack.imgur.com/GY4ae.png)
