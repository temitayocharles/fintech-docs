# Vault Bootstrap Checklist

## Assumptions
- Vault KV v2 enabled at `kv/`
- ESO ClusterSecretStore: `vault-backend`

## Steps
1. Create base path per service in Vault.
1. Add required keys for each service.
1. Verify secrets via `vault kv get`.
1. Ensure ESO ExternalSecrets map to the correct K8s secret names used in Helm.

## Required Keys by Service

### Account Service
Vault path: `kv/fintech/account-service`
Keys: `DATABASE_URL`

### Transaction Service
Vault path: `kv/fintech/transaction-service`
Keys: `DATABASE_URL`

### User Service
Vault path: `kv/fintech/user-service`
Keys: `DATABASE_URL`

### Keycloak Client
Vault path: `kv/fintech/keycloak`
Keys: `CLIENT_SECRET`

### Analytics Service
Vault path: `kv/fintech/analytics-service`
Keys: `INFLUX_TOKEN`

### Audit Service
No secret keys required.

### Notification Service
No secret keys required.

### Frontend
No secret keys required.

## ESO Mapping Reminder
K8s Secret names must match:
- `account-db-secret`
- `transaction-db-secret`
- `user-db-secret`
- `keycloak-client-secret`
- `influxdb-token`
