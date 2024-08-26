# Astra Trident Installation Playbook
This playbook installs Astra Trident, StorageClasses, and Backend using Ansible.

## Overview

This playbook automates the installation of Astra Trident, StorageClasses, and Backend on the local machine. It assumes that the target machine has Ansible, Helm, and Kubectl installed and is configured to connect to the Kubernetes cluster.

## Prerequisites

- Ansible installed on the local machine
- Access to the Kubernetes cluster
- Helm installed on the local machine
- Kubectl Installed on the local machine

## Playbook Steps

1. Create the `trident` namespace in the Kubernetes cluster.
2. Add the Astra Trident Helm repository.
3. Install Trident using Helm, specifying the desired version and namespace.
4. Create the backend using the provided YAML file.
5. Create the storage class using the provided YAML file.

## Customization

### Variables

The playbook uses the following variables, which can be customized by modifying the `defaults/main.yml` file:

- `kubeconfig_path`: Path to the Kubernetes configuration file.
- `trident_version`: Version of Trident to install.
- `backend_file`: Path to the backend YAML file.
- `storageclass_file`: Path to the storage class YAML file.

### Files

The playbook expects the following files to be present in the same directory:

- `defaults/main.yml`: Contains the default variable values.
- `backend_file`: YAML file defining the backend configuration.
- `storageclass_file`: YAML file defining the storage class configuration.
- `kubeconfig_file`: Location of your K8 cluster's config file on your local machine.

Make sure to update the file paths in the playbook if you move or rename these files.

### Running the Playbook

The playbook can be ran using `ansible-playbook trident-install.yml`

## Troubleshooting

- If the playbook fails, make sure you have the necessary permissions and access to the Kubernetes cluster.
- If you are having issues deleting resources, make sure you delete/edit the finalizers for the resources.

## References

- [Astra Trident Documentation](https://netapp-trident.readthedocs.io/)

