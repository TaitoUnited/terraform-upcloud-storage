# UpCloud storage

Example usage:

```
provider "upcloud" {
}

module "storage" {
  source          = "TaitoUnited/storage/upcloud"
  version         = "0.0.1"

  project_id      = "my-infrastructure"
  storage_buckets = yamldecode(file("${path.root}/../infra.yaml"))["storageBuckets"]
}
```

Example YAML:

```
storageBuckets:
  - name: zone1-state
    purpose: state
    location: europe-1
    storageClass: REGIONAL
    versioningEnabled: true
    versioningRetainDays: 60
    lockRetainDays:
    transitionRetainDays:
    transitionStorageClass:
    autoDeletionRetainDays:
    replicationBucket:
    backupRetainDays:
    backupLocation:
    backupLock:
    cdnDomain:
    cors:
    members:

  - name: zone1-locked-backup
    purpose: backup
    location: europe-1
    storageClass: COLDLINE
    versioningEnabled: false
    versioningRetainDays:
    lockRetainDays: 100
    transitionRetainDays:
    transitionStorageClass:
    autoDeletionRetainDays: 0
    replicationBucket:
    backupRetainDays:
    backupLocation:
    backupLock:
    cdnDomain:
    cors:
    members:

  - name: zone1-public
    purpose: public
    location: europe-1
    storageClass: REGIONAL
    versioningEnabled: true
    versioningRetainDays: 60
    lockRetainDays:
    transitionRetainDays:
    transitionStorageClass:
    autoDeletionRetainDays:
    replicationBucket:
    backupRetainDays:
    backupLocation:
    backupLock:
    cdnDomain: cdn.mydomain.com
    corsRules:
      - allowedOrigins: ["*"]
    members:
      - id: "1234567890@cloudbuild.gserviceaccount.com"
        roles: [ "roles/storage.objectCreator" ]
```

Combine with the following modules to get a complete infrastructure defined by YAML:

- [Admin](https://registry.terraform.io/modules/TaitoUnited/admin/upcloud)
- [DNS](https://registry.terraform.io/modules/TaitoUnited/dns/upcloud)
- [Network](https://registry.terraform.io/modules/TaitoUnited/network/upcloud)
- [Compute](https://registry.terraform.io/modules/TaitoUnited/compute/upcloud)
- [Kubernetes](https://registry.terraform.io/modules/TaitoUnited/kubernetes/upcloud)
- [Databases](https://registry.terraform.io/modules/TaitoUnited/databases/upcloud)
- [Storage](https://registry.terraform.io/modules/TaitoUnited/storage/upcloud)
- [Monitoring](https://registry.terraform.io/modules/TaitoUnited/monitoring/upcloud)
- [Integrations](https://registry.terraform.io/modules/TaitoUnited/integrations/upcloud)
- [PostgreSQL privileges](https://registry.terraform.io/modules/TaitoUnited/privileges/postgresql)
- [MySQL privileges](https://registry.terraform.io/modules/TaitoUnited/privileges/mysql)

TIP: Similar modules are also available for AWS, Azure, and DigitalOcean. All modules are used by [infrastructure templates](https://taitounited.github.io/taito-cli/templates#infrastructure-templates) of [Taito CLI](https://taitounited.github.io/taito-cli/). See also [UpCloud Cloud project resources](https://registry.terraform.io/modules/TaitoUnited/project-resources/upcloud), [Full Stack Helm Chart](https://github.com/TaitoUnited/taito-charts/blob/master/full-stack), and [full-stack-template](https://github.com/TaitoUnited/full-stack-template).

Contributions are welcome!
