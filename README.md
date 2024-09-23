# ArgoCD App of Apps Project

This repository implements an ArgoCD App of Apps pattern to deploy Istio and its dependencies, as well as a Flask web application. The repository is structured to house all necessary Kubernetes manifests and ArgoCD application configurations.

## Repository Structure

```
.
├── application-boot.yaml
├── boot
│   ├── Chart.yaml
│   ├── templates
│   │   ├── argocd-crd-boot.yaml
│   │   ├── istio-operator-application.yaml
│   │   ├── istio-operator-boot.yaml
│   │   └── namespace.yaml
│   └── values.yaml
├── cluster-charts
│   ├── argocd-crd-boot
│   │   ├── Chart.yaml
│   │   ├── templates
│   │   │   └── virtualservice.yaml
│   │   └── values.yaml
│   └── istio-operator-boot
│       ├── Chart.yaml
│       ├── templates
│       │   ├── istio-operator.yaml
│       │   └── namespace.yaml
│       └── values.yaml
├── flask
│   ├── Chart.yaml
│   ├── templates
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   └── values.yaml
├── flask.yaml
├── img
│   ├── Screenshot 2024-07-06 184726.png
│   └── Screenshot 2024-07-06 225639.png
└── README.md
```

- boot: Contains ArgoCD application manifests for deploying Istio and its dependencies.
- cluster-charts: Contains Istio configuration files, including virtual services and gateways.
- flask: Contains the deployment and service YAML files for the Flask web application.
- application-boot.yaml: ArgoCD application manifest for bootstrapping Istio and its dependencies.
- flask.yaml: ArgoCD application manifest for deploying the Flask web application.

## Prerequisites

- [ArgoCD](https://gitlab.com/assessment4622826/terraform-eks-argocd.git)
- [Flask App and pipeline](https://gitlab.com/assessment4622826/hello_world_app.git)

## Bootstrapping Istio and dependencies

1. **Apply the boot.yaml manifest**:

    ```sh
    kubectl apply -f application-boot.yaml
    ```

    This will deploy the Istio control plane and its dependencies using ArgoCD.

2. **Verify the deployment**:

    ```sh
    kubectl get pods -n istio-system
    ```

    Ensure all Istio components are running successfully.

### Deploying the Flask Web Application

1. **Apply the flask.yaml manifest**:

    ```sh
    kubectl apply -f flask.yaml
    ```
### Connect To ArgoCD

https://gitlab.com/assessment4622826/terraform-eks-argocd

## ArgoCD Applications

1. **Check ArgoCD UI**:
    - Open the ArgoCD UI and verify that the applications are correctly synchronized and deployed
    ![alt text](img/Screenshot 2024-07-06 184726.png)
