# ansible-kubeflow
[![Build Status](https://travis-ci.org/andiveloper/ansible-kubeflow.svg?branch=master)](https://travis-ci.org/andiveloper/ansible-kubeflow)

An Ansible Galaxy role that can be used to deploy [kubeflow](https://www.kubeflow.org) on an existing Kubernetes cluster

To get started specify at least one node of your Kubernetes cluster and assign it the variable `kfctl=True`

Sample inventory.ini:

```
# vm12 is a Kubernetes node

[kfctl]
vm12

[kfctl:vars]
kfctl=True
```

Other variables that can be changed and their defaults (see also under `/defaults/main.yaml`):

```
kubeflow_config_url: https://raw.githubusercontent.com/kubeflow/manifests/v0.7-branch/kfdef/kfctl_k8s_istio.0.7.0.yaml
kubeflow_deployment_name: my-kubeflow
kubeflow_target_dir: /opt/kubeflow
kfctl_package_url: https://github.com/kubeflow/kubeflow/releases/download/v0.7.0/kfctl_v0.7.0_linux.tar.gz
```

After deployment you can access the UI by finding the IP of centraldashboard service, the default port is 80:

```
[root@vm12 ~]# kubectl get service/centraldashboard -n kubeflow
NAME               TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)   AGE
centraldashboard   ClusterIP   10.100.242.237   <none>        80/TCP    33m
```

You can then either deploy an EXTERNAL-IP or access the UI via a ssh tunnel on your local machine, e.g.:

```
# vm12 is my kubernetes node
# 10.100.242.237 is the IP of my centraldashboard service

ssh vm12 -L 18080:10.100.242.237:80 -v -N

# The UI can then be accessed by navigating to http://localhost:18080
```
