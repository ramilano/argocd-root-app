# ArgoCD Root Application

This Helm chart manages ArgoCD root applications that deploy and manage child applications from external Git repositories.

## Overview

The chart creates ArgoCD Application resources that point to external repositories containing application configurations. This follows the "app of apps" pattern commonly used with ArgoCD.

## Structure

- `Chart.yaml` - Helm chart metadata
- `values.yml` - Configuration values for the chart
- `templates/demo-app.yaml` - Example ArgoCD Application manifest

## Usage

### Install the chart

```bash
helm install argo-root-app . -n argocd
```

### Template the chart

```bash
helm template argo-root-app . -n argocd
```

### Validate the chart

```bash
helm lint .
```

## Configuration

The chart uses values from `values.yml` to configure:
- Kubernetes cluster destination server
- Target revision for source repositories
- Namespace destinations for applications

## Adding New Applications

To add a new application, create a new YAML file in the `templates/` directory following the pattern in `demo-app.yaml`:

1. Define an ArgoCD Application resource
2. Reference the external Git repository containing your application
3. Use Helm templating for common values like destination server
4. Configure sync policies as needed