# Kubernetes Deployment with Ansible

This Ansible playbook automates the deployment of applications to Kubernetes clusters.

## Prerequisites

- Ansible 2.9+
- kubectl configured to communicate with your Kubernetes cluster
- Access to the Kubernetes control plane node

## Directory Structure

```
ansible/
├── inventory.ini                # Inventory file with target hosts
├── kubernetes-deployment.yaml   # Main playbook file
└── roles/
    └── kubernetes/             # Kubernetes role
        ├── tasks/              # Tasks for Kubernetes deployment
        ├── templates/          # Kubernetes manifest templates
        └── vars/               # Variables for the deployment
```

## Configuration

Edit the following files to customize your deployment:

- `roles/kubernetes/vars/main.yml` - Configure application details, resource limits, etc.
- `inventory.ini` - Update with your Kubernetes control plane and node details

## Usage

Run the playbook with:

```bash
ansible-playbook -i inventory.ini kubernetes-deployment.yaml
```

## Customization

To deploy a different application, update the variables in `roles/kubernetes/vars/main.yml`:

- `application_name`: Name of your application
- `application_image`: Docker image for your application
- `application_replicas`: Number of replicas
- `kubernetes_namespace`: Kubernetes namespace for deployment

You can also customize resource limits, environment variables, and other settings in the variables file. 