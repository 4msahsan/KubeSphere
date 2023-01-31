 <h1> KubeSphere Setup on Ubuntu 22.04 </h1>
<pre>

root@kubesphere:~# ./kk create cluster --with-kubernetes v1.24.2 --with-kubesphere v3.3.1 --container-manager containerd

<b>
 _   __      _          _   __
| | / /     | |        | | / /
| |/ / _   _| |__   ___| |/ /  ___ _   _
|    \| | | | '_ \ / _ \    \ / _ \ | | |
| |\  \ |_| | |_) |  __/ |\  \  __/ |_| |
\_| \_/\__,_|_.__/ \___\_| \_/\___|\__, |
                                    __/ |
                                   |___/

</b>
16:54:33 UTC [GreetingsModule] Greetings
16:54:34 UTC message: [kubesphere]
Greetings, KubeKey!
16:54:34 UTC success: [kubesphere]
16:54:34 UTC [NodePreCheckModule] A pre-check on nodes
16:54:34 UTC success: [kubesphere]
16:54:34 UTC [ConfirmModule] Display confirmation form
+------------+------+------+---------+----------+-------+-------+---------+-----------+--------+--------+------------+------------+-------------+------------------+--------------+
| name       | sudo | curl | openssl | ebtables | socat | ipset | ipvsadm | conntrack | chrony | docker | containerd | nfs client | ceph client | glusterfs client | time         |
+------------+------+------+---------+----------+-------+-------+---------+-----------+--------+--------+------------+------------+-------------+------------------+--------------+
| kubesphere | y    | y    | y       | y        | y     | y     |         | y         |        |        |            |            |             |                  | UTC 16:54:34 |
+------------+------+------+---------+----------+-------+-------+---------+-----------+--------+--------+------------+------------+-------------+------------------+--------------+

This is a simple check of your environment.
Before installation, ensure that your machines meet all requirements specified at
https://github.com/kubesphere/kubekey#requirements-and-recommendations

Continue this installation? [yes/no]: yes
16:54:36 UTC success: [LocalHost]
16:54:36 UTC [NodeBinariesModule] Download installation binaries
16:54:36 UTC message: [localhost]
downloading amd64 kubeadm v1.24.2 ...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 42.3M  100 42.3M    0     0  8854k      0  0:00:04  0:00:04 --:--:-- 8854k
16:54:42 UTC message: [localhost]
downloading amd64 kubelet v1.24.2 ...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  110M  100  110M    0     0  9424k      0  0:00:12  0:00:12 --:--:-- 9823k

bootstrap-token] Configured RBAC rules to allow certificate rotation for all node client certificates in the cluster
[bootstrap-token] Creating the "cluster-info" ConfigMap in the "kube-public" namespace
[kubelet-finalize] Updating "/etc/kubernetes/kubelet.conf" to point to a rotatable kubelet client certificate and key
[addons] Applied essential addon: CoreDNS
[addons] Applied essential addon: kube-proxy

Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

You can now join any number of control-plane nodes by copying certificate authorities
and service account keys on each node and then running the following as root:

  kubeadm join lb.kubesphere.local:6443 --token 2v01wi.unqqwo3trrwxuxgx \
        --discovery-token-ca-cert-hash sha256:4ca2fe36497c7487d522517114c2f9a43d0caabc55612bbb76b6695c84a181f8 \
        --control-plane

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join lb.kubesphere.local:6443 --token 2v01wi.unqqwo3trrwxuxgx \
        --discovery-token-ca-cert-hash sha256:4ca2fe36497c7487d522517114c2f9a43d0caabc55612bbb76b6695c84a181f8
16:57:46 UTC success: [kubesphere]


daemonset.apps/calico-node created
serviceaccount/calico-node created
deployment.apps/calico-kube-controllers created
serviceaccount/calico-kube-controllers created
poddisruptionbudget.policy/calico-kube-controllers created
16:57:53 UTC success: [kubesphere]
16:57:53 UTC [ConfigureKubernetesModule] Configure kubernetes
16:57:53 UTC success: [kubesphere]
16:57:53 UTC [ChownModule] Chown user $HOME/.kube dir
16:57:53 UTC success: [kubesphere]
16:57:53 UTC [AutoRenewCertsModule] Generate k8s certs renew script
16:57:53 UTC success: [kubesphere]
16:57:53 UTC [AutoRenewCertsModule] Generate k8s certs renew service
16:57:53 UTC success: [kubesphere]
16:57:53 UTC [AutoRenewCertsModule] Generate k8s certs renew timer
16:57:53 UTC success: [kubesphere]
16:57:53 UTC [AutoRenewCertsModule] Enable k8s certs renew service
16:57:54 UTC success: [kubesphere]
16:57:54 UTC [SaveKubeConfigModule] Save kube config as a configmap
16:57:54 UTC success: [LocalHost]
16:57:54 UTC [AddonsModule] Install addons
16:57:54 UTC success: [LocalHost]
16:57:54 UTC [DeployStorageClassModule] Generate OpenEBS manifest
16:57:54 UTC success: [kubesphere]
16:57:54 UTC [DeployStorageClassModule] Deploy OpenEBS as cluster default StorageClass
16:57:55 UTC success: [kubesphere]
16:57:55 UTC [DeployKubeSphereModule] Generate KubeSphere ks-installer crd manifests
16:57:55 UTC success: [kubesphere]
16:57:55 UTC [DeployKubeSphereModule] Apply ks-installer
16:57:57 UTC stdout: [kubesphere]
namespace/kubesphere-system created
serviceaccount/ks-installer created
customresourcedefinition.apiextensions.k8s.io/clusterconfigurations.installer.kubesphere.io created
clusterrole.rbac.authorization.k8s.io/ks-installer created
clusterrolebinding.rbac.authorization.k8s.io/ks-installer created
deployment.apps/ks-installer created
16:57:57 UTC success: [kubesphere]
16:57:57 UTC [DeployKubeSphereModule] Add config to ks-installer manifests
16:57:57 UTC success: [kubesphere]
16:57:57 UTC [DeployKubeSphereModule] Create the kubesphere namespace
16:57:57 UTC success: [kubesphere]
16:57:57 UTC [DeployKubeSphereModule] Setup ks-installer config
16:57:57 UTC stdout: [kubesphere]
secret/kube-etcd-client-certs created
16:57:57 UTC success: [kubesphere]
16:57:57 UTC [DeployKubeSphereModule] Apply ks-installer
16:57:58 UTC stdout: [kubesphere]
namespace/kubesphere-system unchanged
serviceaccount/ks-installer unchanged
customresourcedefinition.apiextensions.k8s.io/clusterconfigurations.installer.kubesphere.io unchanged
clusterrole.rbac.authorization.k8s.io/ks-installer unchanged
clusterrolebinding.rbac.authorization.k8s.io/ks-installer unchanged
deployment.apps/ks-installer unchanged
clusterconfiguration.installer.kubesphere.io/ks-installer created
16:57:58 UTC success: [kubesphere]
#####################################################
###              Welcome to KubeSphere!           ###
#####################################################

Console: http://192.168.0.151:30880
Account: admin
Password: P@88w0rd
NOTES：
  1. After you log into the console, please check the
     monitoring status of service components in
     "Cluster Management". If any service is not
     ready, please wait patiently until all components
     are up and running.
  2. Please change the default password after login.

#####################################################
https://kubesphere.io             2023-01-30 17:11:56
#####################################################
17:12:01 UTC success: [kubesphere]
17:12:01 UTC Pipeline[CreateClusterPipeline] execute successfully
Installation is complete.

Please check the result using the command:
<b>
        kubectl logs -n kubesphere-system $(kubectl get pod -n kubesphere-system -l 'app in (ks-install, ks-installer)' -o jsonpath='{.items[0].metadata.name}') -f
</b>
root@kubesphere:~#


root@kubesphere:~# kubectl logs -n kubesphere-system $(kubectl get pod -n kubesphere-system -l 'app in (ks-install, ks-installer)' -o jsonpath='{.items[0].metadata.name}') -f | more
2023-01-30T16:58:47Z INFO     : shell-operator latest
2023-01-30T16:58:47Z INFO     : HTTP SERVER Listening on 0.0.0.0:9115
2023-01-30T16:58:47Z INFO     : Use temporary dir: /tmp/shell-operator
2023-01-30T16:58:47Z INFO     : Initialize hooks manager ...
2023-01-30T16:58:47Z INFO     : Search and load hooks ...
2023-01-30T16:58:47Z INFO     : Load hook config from '/hooks/kubesphere/installRunner.py'
2023-01-30T16:58:48Z INFO     : Load hook config from '/hooks/kubesphere/schedule.sh'
2023-01-30T16:58:48Z INFO     : Initializing schedule manager ...
2023-01-30T16:58:48Z INFO     : KUBE Init Kubernetes client
2023-01-30T16:58:48Z INFO     : KUBE-INIT Kubernetes client is configured successfully
2023-01-30T16:58:48Z INFO     : MAIN: run main loop
2023-01-30T16:58:48Z INFO     : MAIN: add onStartup tasks
2023-01-30T16:58:48Z INFO     : Running schedule manager ...
2023-01-30T16:58:48Z INFO     : QUEUE add all HookRun@OnStartup
2023-01-30T16:58:48Z INFO     : MSTOR Create new metric shell_operator_live_ticks
2023-01-30T16:58:48Z INFO     : MSTOR Create new metric shell_operator_tasks_queue_length
2023-01-30T16:58:48Z INFO     : GVR for kind 'ClusterConfiguration' is installer.kub

tart installing openpitrix
Start installing network
**************************************************
Waiting for all tasks to be completed ...
task network status is successful  (1/4)
task openpitrix status is successful  (2/4)
task multicluster status is successful  (3/4)
task monitoring status is successful  (4/4)
**************************************************
Collecting installation results ...
#####################################################
###              Welcome to KubeSphere!           ###
#####################################################

Console: http://192.168.0.151:30880
Account: admin
Password: P@88w0rd
NOTES：
  1. After you log into the console, please check the
     monitoring status of service components in
     "Cluster Management". If any service is not
     ready, please wait patiently until all components
     are up and running.
  2. Please change the default password after login.



<b>root@kubesphere:~/YML# kubectl get pods -n kube-system</b>
NAME                                           READY   STATUS    RESTARTS   AGE
calico-kube-controllers-5cc4cdb7ff-nznzt       1/1     Running   0          36m
calico-node-s6nl5                              1/1     Running   0          36m
coredns-fb4b8cf5c-hc69d                        1/1     Running   0          36m
coredns-fb4b8cf5c-xck58                        1/1     Running   0          36m
kube-apiserver-kubesphere                      1/1     Running   0          36m
kube-controller-manager-kubesphere             1/1     Running   0          36m
kube-proxy-grqfz                               1/1     Running   0          36m
kube-scheduler-kubesphere                      1/1     Running   0          36m
nodelocaldns-lgxq9                             1/1     Running   0          36m
openebs-localpv-provisioner-5778dcd6c6-88dsp   1/1     Running   0          36m
snapshot-controller-0                          1/1     Running   0          34m
root@kubesphere:~/YML#


<h2>************* Nginx deployment *********</h2>
<b>
root@kubesphere:~/YML# kubectl create deployment msa-nginx --image=nginx
deployment.apps/msa-nginx created
root@kubesphere:~/YML# kubectl get deploy
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
msa-nginx   0/1     1            0           8s
root@kubesphere:~/YML# kubectl get deploy


root@kubesphere:~/YML# kubectl get deploy -o wide
NAME        READY   UP-TO-DATE   AVAILABLE   AGE   CONTAINERS   IMAGES   SELECTOR
msa-nginx   1/1     1            1           38s   nginx        nginx    app=msa-nginx
root@kubesphere:~/YML#

root@kubesphere:~/YML# kubectl scale deployment msa-nginx --replicas=3
deployment.apps/msa-nginx scaled
root@kubesphere:~/YML# kubectl get deploy -o wide
NAME        READY   UP-TO-DATE   AVAILABLE   AGE   CONTAINERS   IMAGES   SELECTOR
msa-nginx   2/3     3            2           10m   nginx        nginx    app=msa-nginx
root@kubesphere:~/YML#

root@kubesphere:~/YML# kubectl scale deployment msa-nginx --replicas=3
deployment.apps/msa-nginx scaled
root@kubesphere:~/YML# kubectl get deploy -o wide
NAME        READY   UP-TO-DATE   AVAILABLE   AGE   CONTAINERS   IMAGES   SELECTOR
msa-nginx   2/3     3            2           10m   nginx        nginx    app=msa-nginx
root@kubesphere:~/YML# kubectl expose deployment msa-nginx --type="NodePort" --port 80
service/msa-nginx exposed
root@kubesphere:~/YML# kubectl get svc
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)        AGE
kubernetes   ClusterIP   10.233.0.1   <none>        443/TCP        69m
msa-nginx    NodePort    10.233.1.8   <none>        80:32250/TCP   5s
root@kubesphere:~/YML#

root@kubesphere:~/YML# kubectl get svc
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)        AGE
kubernetes   ClusterIP   10.233.0.1   <none>        443/TCP        69m
msa-nginx    NodePort    10.233.1.8   <none>        80:32250/TCP   5s
root@kubesphere:~/YML# curl
10.233.1.8
root@kubesphere:~/YML# curl 10.233.1.8
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@kubesphere:~/YML#
</b>
</pre>

