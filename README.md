# Fintech Docs


## Start Here
- Read [START_HERE.md](START_HERE.md) for the chronological playbook.


## Documentation Index
- [FIRST_CLUSTER_DEPLOYMENT.md](FIRST_CLUSTER_DEPLOYMENT.md)
- [HELM_QUICKSTART.md](HELM_QUICKSTART.md)
- [RUNBOOKS.md](RUNBOOKS.md)
- [VAULT_BOOTSTRAP_CHECKLIST.md](VAULT_BOOTSTRAP_CHECKLIST.md)
- [VAULT_ESO_MAPPING.md](VAULT_ESO_MAPPING.md)

## Start Here (Playbook)
1. Read the platform overview and service map in this repo.
1. Pick one service repo and open its README playbook.
1. Create local config values from the service README, then run tests.
1. Push to `main` to trigger CI and publish to GHCR.
1. Confirm Argo CD syncs the service Helm chart from `fintech-gitops`.
1. Verify `/health` and basic UI routes in the cluster.

## Core Documents
- [Vault + ESO Mapping](VAULT_ESO_MAPPING.md)
- [Vault Bootstrap Checklist](VAULT_BOOTSTRAP_CHECKLIST.md)
- [Helm Quick-Start](HELM_QUICKSTART.md)
- [First Cluster Deployment](FIRST_CLUSTER_DEPLOYMENT.md)
- [Operations Runbooks](RUNBOOKS.md)

## Services
- [Account Service](https://github.com/temitayocharles/fintech-account-service)
- [Transaction Service](https://github.com/temitayocharles/fintech-transaction-service)
- [User Service](https://github.com/temitayocharles/fintech-user-service)
- [Audit Service](https://github.com/temitayocharles/fintech-audit-service)
- [Notification Service](https://github.com/temitayocharles/fintech-notification-service)
- [Analytics Service](https://github.com/temitayocharles/fintech-analytics-service)
- [Frontend](https://github.com/temitayocharles/fintech-frontend)

## GitOps
- [Fintech GitOps](https://github.com/temitayocharles/fintech-gitops)
- Charts live per service at `fintech-gitops/apps/<service>/chart`.
- Argo CD sync is automated per environment.
- Image tags are auto‑updated in `fintech-gitops` via Argo Image Updater.

## Infrastructure
- [Fintech Infra](https://github.com/temitayocharles/fintech-infra)
