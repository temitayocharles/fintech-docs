# First Cluster Deployment (End-to-End)

This playbook assumes Argo CD is installed and has access to the `fintech-gitops` repo.

## 1. Verify Cluster Prerequisites
1. Kubernetes cluster is reachable.
1. Ingress controller installed.
1. Storage class available.
1. Vault + ESO installed.
1. Argo CD installed.

## 2. Bootstrap Vault Secrets
1. Use the Vault Bootstrap Checklist in `fintech-docs/VAULT_BOOTSTRAP_CHECKLIST.md`.
1. Ensure ESO has created the required K8s secrets.

## 3. Verify GitOps Repo Access
1. Confirm Argo CD has access to `fintech-gitops`.
1. Confirm ApplicationSets are present for dev/staging/prod.

## 4. Deploy Services (Automated Sync)
1. Ensure `fintech-services-dev` ApplicationSet exists.
1. Argo CD will auto‑sync all service charts from `fintech-gitops`.
1. Wait for all apps to reach `Healthy` + `Synced`.

## 5. Verify Runtime
1. `kubectl get pods -n banking-system`
1. `kubectl get svc -n banking-system`
1. Confirm `/health` endpoints for each service.

## 6. Roll Forward / Rollback
- Roll forward by pushing code to `main`.
- Roll back by pinning image tag in `values-<env>.yaml` in `fintech-gitops`.

## 7. Common Issues
- Missing secrets: ESO sync not creating K8s secrets.
- Image tag mismatch: check `values-<env>.yaml` and GitOps dispatch logs.
- Pod crash: check logs and validate env vars.
