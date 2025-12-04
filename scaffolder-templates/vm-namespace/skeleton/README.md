# ${{values.namespace_id}} Namespace GitOps Repository

This repository contains the GitOps configuration for the `${{values.namespace_id}}` namespace.

## Overview

- **Namespace**: `${{values.namespace_id}}`
- **Environment**: `${{values.environment}}`
- **Owner**: `${{values.owner}}`
- **Cluster**: `${{values.cluster_id}}`

## Structure

```
manifests/
├── namespace/          # Namespace definition
│   └── namespace.yaml
└── vms/               # VM manifests (added via templates)
    └── README.md
```

## ArgoCD Application

This repository is managed by the ArgoCD Application: `${{values.namespace_id}}-env`

- **Application**: https://openshift-gitops-server-openshift-gitops${{values.cluster_id}}/applications/${{values.namespace_id}}-env
- **Namespace**: https://console-openshift-console${{values.cluster_id}}/k8s/cluster/projects/${{values.namespace_id}}

## Adding Resources

### Add VMs
Use the "Add VM to Namespace" template in Developer Hub to add VMs to this namespace.

### Add other resources manually
1. Create your Kubernetes manifests in the appropriate subdirectory under `manifests/`
2. Commit and push to the `main` branch
3. ArgoCD will automatically sync the changes to the cluster

## Sync Waves

Resources are applied in order based on sync-wave annotations:
- `-1`: Namespace (created first)
- `0`: Default for VMs and other resources
