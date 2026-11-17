# GitOps Lab Repository

This repository demonstrates GitOps workflows using OpenShift GitOps (Argo CD) and Kustomize.

## Repository Structure

```text
├── apps/
│   └── guestbook/
│       ├── base/
│       │   ├── deployment.yaml
│       │   ├── service.yaml
│       │   ├── route.yaml
│       │   └── kustomization.yaml
│       └── overlays/
│           ├── dev/
│           │   └── kustomization.yaml     # 1 replica, APP_ENV=development, namespace: gitops-dev
│           └── prod/
│               └── kustomization.yaml    # 2 replicas, APP_ENV=production, namespace: gitops-prod
└── argo-apps/
    ├── guestbook-dev.yaml                 # Argo CD Application for Dev
    └── guestbook-prod.yaml                # Argo CD Application for Prod
```

## Environments

| Environment | Namespace | Replicas | Environment Variable (`APP_ENV`) | Route Host |
| :--- | :--- | :--- | :--- | :--- |
| **Dev** | `gitops-dev` | 1 | `development` | `guestbook-ui-gitops-dev.apps.ocp4.navy.mil` |
| **Prod** | `gitops-prod` | 2 | `production` | `guestbook-ui-gitops-prod.apps.ocp4.navy.mil` |
