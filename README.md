# Fintech Docs

## Start Here
1. Pick the service you want to work on.
1. Open that service repo README and follow its playbook.
1. Use `.env.example` in that repo to map config keys to Vault secrets.
1. Run tests locally and then push to `main` to trigger CI and image builds.
1. Argo CD auto-syncs Helm charts from `fintech-gitops`.

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
- Helm charts live per service in `fintech-gitops/apps/<service>/chart`.
- Argo CD sync is automated for dev, staging, and prod.

## Infrastructure
- [Fintech Infra](https://github.com/temitayocharles/fintech-infra)
