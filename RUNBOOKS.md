# Operations Runbooks

## Argo CD Sync Troubleshooting
1. Open Argo CD UI and locate the application.
1. If status is `OutOfSync`, click `Sync` to re-apply desired state.
1. If status is `Degraded`, open the application and inspect pod events and logs.
1. Validate image tags in `fintech-gitops/apps/<service>/chart/values-<env>.yaml`.
1. Confirm K8s secrets exist for all Vault-backed values.

## Rollback to Previous Image
1. Open `fintech-gitops/apps/<service>/chart/values-<env>.yaml`.
1. Set `image.tag` to the previous SHA or release tag.
1. Commit and push to `main`.
1. Argo CD will auto-sync back to the pinned version.

## Pin Image to Prevent Auto Updates
1. In `fintech-gitops/apps/<service>/chart/values-<env>.yaml`, set `image.tag` to a fixed tag.
1. Pause the CI dispatch for that service if needed.
1. Re-enable auto updates by returning to `latest` or by allowing repo-dispatch updates.

## Force Redeploy (No Code Changes)
1. Re-run the service CI/CD pipeline in GitHub Actions.
1. Confirm a new image tag is published to GHCR.
1. Verify GitOps tag bump commit in `fintech-gitops`.

## Incident Quick Checks
1. `kubectl get pods -n banking-system`
1. `kubectl describe pod <pod> -n banking-system`
1. `kubectl logs -f deployment/<service> -n banking-system`
1. Verify Vault secrets exist for the service.
