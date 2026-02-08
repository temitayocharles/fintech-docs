# Helm Quick-Start (Local Validation)

## Prerequisites
- Helm installed
- Access to `fintech-gitops`

## Lint a Chart
```bash
helm lint fintech-gitops/apps/<service>/chart
```

## Render Manifests (Dev)
```bash
helm template <service> fintech-gitops/apps/<service>/chart   -f fintech-gitops/apps/<service>/chart/values.yaml   -f fintech-gitops/apps/<service>/chart/values-dev.yaml
```

## Render Manifests (Staging)
```bash
helm template <service> fintech-gitops/apps/<service>/chart   -f fintech-gitops/apps/<service>/chart/values.yaml   -f fintech-gitops/apps/<service>/chart/values-staging.yaml
```

## Render Manifests (Prod)
```bash
helm template <service> fintech-gitops/apps/<service>/chart   -f fintech-gitops/apps/<service>/chart/values.yaml   -f fintech-gitops/apps/<service>/chart/values-prod.yaml
```

## Troubleshooting
- If values do not appear in `envFrom`, confirm `configmap.yaml` is rendered.
- If secrets are missing, verify ESO has created the secret names referenced in values.
