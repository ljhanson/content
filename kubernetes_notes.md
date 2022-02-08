Title: Kubernetes Notes
Date: 9/13/2019 10:16 PM
Author: L.J. Hanson
Tags: docker, kubernetes, linux,
Slug: Your Kubernetes control-plane has initialized successfully!

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

What is a pod?

* Defines one or more containers
  * How they run
  * Resources needed
* Kubernetes manages pods, NOT containers
* Most applications use one application per pod
* Containers in same pod talk via localhost

Multi container pods

* Containers in same pod scaled identically, can be an issue for apps like database.
* Only group tightly coupled services into a pod.
* initContainers may contain software, passwords or secrets only used for startup
  * May allow you to use other images without changes
  * Example: Static site generator feeding output to volume which is then mounted at document root for web server.
  * Delay start of rest of service until they are complete.

Networking:

* NetworkPolicy defines external access to pods within the cube
  * CIDR Blocks
  * App labels
  * Ports
* Blank policies block everything
* Policy of {} allows all
* [Network Docs](https://kubernetes.io/docs/concepts/services-networking/network-policies/)

Controllers:

* Abstraction layer on top of pods
* They create and manage pods

|Types|Role|
|:---|:---|
|Deployment|Manage long running pods|
|StatefulSet| Deployment with order and uniqueness|
|DaemonSet|Run a replica on every node|
|Job|Run a one-off job to completion|
|CronJob|Run job according to schedule|

Services:

| Type | Purpose |
|:---|:---|
|ClusterIP | Assigned an IP in cluster, but not externally available |
| NodePort | Published port on every node in cluster |
| LoadBalancer | Used with Cloud providers to create an external load balancer|
| ExternalName | Provides a DNS alias to an external host name |

Secrets & ConfgMaps:

* Secrets base64 encoded in config, viewable as plain text in pod
* Use RBAC to protect
* ConfgMaps primarily for config data

Volumes:

* Typically creed to be created before use
* RO or RW
* Plain Volumes are deleted with pod, underlying storage may remain
* [Volume Docs](https://kubernetes.io/docs/concepts/storage/volumes/)
