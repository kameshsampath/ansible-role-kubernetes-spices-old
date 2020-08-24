# Ansible role for Spicing Kubernetes Cluster with Apps

Ansible to create [KinD](https://kind.sigs.k8s.io)  or [minikube](https://minikube.sigs.k8s.io) cluster. 

The role can also be used to install and configure:

- [x] Default [Ingress](https://kind.sigs.k8s.io/docs/user/ingress/#contour) 

- [x] [Knative](https://knative.dev), both Serving and Eventing

- [x] [Tekton](https://tekton.dev)

## Requirements

- [Docker Desktop](https://www.docker.com/products/docker-desktop) or Docker for Linux

- [Ansible](https://ansible.com) >= v2.9.10

```shell
pip3 install \
  -r https://raw.githubusercontent.com/kameshsampath/kameshsampath.k8s_app_spices/master/requirements.txt
ansible-galaxy role install kameshsampath.kind
ansible-galaxy collection install community.kubernetes
```

__NOTE__: For Windows its recommended to use Windows Subsystem for Linux (WSL)

## Role Dependencies

- kameshsampath.minikube or kameshsampath.kind

## Role Variables

| Variable Name| Description | Default |
|--|--|--|
| kubernetes_cluster_type | The Kubernetes Cluster Type minikube or kind or custom | minikube |
| k8s_cluster_ip | The Kubernetes Cluster IP | Auto configured for minikube or KinD |
| deploy_knative | Deploy Knative | False |
| knative_version | The Knative version | v0.16.0 |
| knative_serving_version | The Knative Serving version | v0.16.0 |
| knative_eventing_version | The Knative Eventing version | v0.16.0 |
| deploy_ingress | Deploy Ingress | True |
| ingress_namespace | The namespace for Contour Ingress | contour-system |
| ingress_namespace | The namespace for Contour Ingress | contour-system |
| ingress_manifest  | The Contour Ingress manifest file  | [Project Contour](https://projectcontour.io/quickstart/contour.yaml) |
| deploy_tektoncd | Deploy Tektoncd | False |
| tektoncd_pipelines_version | Tektoncd Pipelines Version | v0.11.3 |
| tektoncd_triggers_version | Tektoncd Triggers Version | v0.4.0 |
| deploy_argocd | Deploy [Argo CD](https://argoproj.github.io/) | False |
| argocd_namespace | Argo CD namespace | argocd |

## Example Playbooks

The [examples](https://github.com/kameshsampath/kameshsampath.k8s_app_spices/tree/master/examples) directory has various playbook examples to get started using this role

## License

[Apache v2](https://github.com/kameshsampath/kameshsampath.k8s_app_spices/tree/master/LICENSE)

## Author Information

[Kamesh Sampath](mailto:kamesh.sampath@hotmail.com)

## Issues

[Issues](https://github.com/kameshsampath/kameshsampath.k8s_app_spices/issues)

## Testing

## Requirements

- Extra Python modules

```shell
pip3 install \
  -r https://raw.githubusercontent.com/kameshsampath/kameshsampath.k8s_app_spices/master/molecule/requirements.txt
ansible-galaxy role install  -r https://raw.githubusercontent.com/kameshsampath/kameshsampath.k8s_app_spices/master/molecule/requirements.txt
```

All tests are built using [molecule](https://molecule.readthedocs.io/en/latest/index.html) with following scenarios:

- default

```shell
molecule test
```

- Ingress

```shell
molecule test  -s deploy_ingress
```

- Knative

```shell
molecule test  -s deploy_knative
```

- Tektoncd

```shell
molecule test  -s deploy_tektoncd
```
