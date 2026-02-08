# Vault + ESO Mapping Matrix

This is the reference mapping between service env keys, Vault entries, and the Kubernetes Secret names consumed by Helm charts.

## Vault Conventions
- KV engine: `kv`
- Suggested path pattern: `kv/fintech/<service>`
- ESO creates K8s secrets per service from Vault paths.

## Services

### Account Service
- Vault path: `kv/fintech/account-service`
- K8s Secret: `account-db-secret`
- Keys:
- `DATABASE_URL`

### Transaction Service
- Vault path: `kv/fintech/transaction-service`
- K8s Secret: `transaction-db-secret`
- Keys:
- `DATABASE_URL`

### User Service
- Vault path: `kv/fintech/user-service`
- K8s Secret: `user-db-secret`
- Keys:
- `DATABASE_URL`
- Vault path: `kv/fintech/keycloak`
- K8s Secret: `keycloak-client-secret`
- Keys:
- `CLIENT_SECRET`

### Analytics Service
- Vault path: `kv/fintech/analytics-service`
- K8s Secret: `influxdb-token`
- Keys:
- `INFLUX_TOKEN`

### Audit Service
- Vault path: `kv/fintech/audit-service`
- K8s Secret: none (no secret keys required)

### Notification Service
- Vault path: `kv/fintech/notification-service`
- K8s Secret: none (no secret keys required)

### Frontend
- Vault path: `kv/fintech/frontend`
- K8s Secret: none (no secret keys required)

## ESO Example (Pattern)
- `secretStoreRef.name`: `vault-backend`
- `dataFrom` or `data` should target `kv/fintech/<service>`
- Generated K8s secret name must match the Helm values secret name.
