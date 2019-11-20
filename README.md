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
