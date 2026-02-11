# Start Here

This guide is the shortest path to run, deploy, and maintain **fintech-docs**.

## 1. What This Repo Is
This is the **fintech-docs** service.

## 2. Repo Map (What Lives Where)
- [README.md](README.md): High‑level overview and endpoints.
- Docker: [Dockerfile](Dockerfile)

## 3. Local Run
Use README for local run steps.



## 5. Config and Secrets
Use Vault for secrets and the configurations repo for ConfigMaps. If you add envs, create `.env.example`.

## 6. Kubernetes / Helm
- Charts live in the **helm-charts** repo under `applications/fintech-docs`.
- Values live in **platform-gitops** under `applications/fintech/fintech-docs`.
- ConfigMaps live in the **configurations** repo.

Typical order:
1. Apply configs.
1. Ensure Vault/ESO secrets exist.
1. Sync the Argo app.

## 7. CI/CD
Check `.github/workflows` for pipelines. These repos typically use shared workflows.

## 8. Troubleshooting
- If health checks fail, check logs and service env vars.
- If DB errors, verify the Vault secret path and ExternalSecret.
