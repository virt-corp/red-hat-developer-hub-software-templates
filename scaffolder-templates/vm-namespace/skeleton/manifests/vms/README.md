# VMs Directory

This directory will contain VM manifests for the `${{values.namespace_id}}` namespace.

## Adding VMs

Use the "Add VM to Namespace" template in Developer Hub to add new VMs to this namespace.

VMs will be created as subdirectories here, each containing:
- VirtualMachine manifest
- Service manifest
- ConfigMaps/Secrets as needed

All VMs in this directory will be managed by the `${{values.namespace_id}}-env` ArgoCD Application.
