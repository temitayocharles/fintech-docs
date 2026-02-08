# Operations Runbooks

## Argo CD Sync Troubleshooting
1. Open Argo CD UI and locate the application.
1. If status is `OutOfSync`, click `Sync` to re-apply desired state.
1. If status is `Degraded`, inspect pod events and logs.
1. Validate image tags in `fintech-gitops/apps/<service>/chart/values-<env>.yaml`.
1. Confirm K8s secrets exist for all Vault-backed values.

## Rollback to Previous Image
1. Open `fintech-gitops/apps/<service>/chart/values-<env>.yaml`.
1. Set `image.tag` to the previous SHA or release tag.
1. Commit and push to `main`.
1. Argo CD auto-syncs back to the pinned version.

## Pin Image to Prevent Auto Updates
1. In `fintech-gitops/apps/<service>/chart/values-<env>.yaml`, set `image.tag` to a fixed tag.
1. Pause Argo Image Updater if required.
1. Re-enable auto updates by returning to moving tags or re-enabling the updater.

## Force Redeploy (No Code Changes)
1. Re-run the service CI/CD pipeline in GitHub Actions.
1. Confirm a new image tag is published to GHCR.
1. Verify GitOps tag bump commit in `fintech-gitops`.

## Incident Quick Checks
1. `kubectl get pods -n fintech`
1. `kubectl describe pod <pod> -n fintech`
1. `kubectl logs -f deployment/<service> -n fintech`
1. Verify Vault secrets exist for the service.
