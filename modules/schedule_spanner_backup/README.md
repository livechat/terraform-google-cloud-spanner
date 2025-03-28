# terraform-google-cloud-spanner

This module was generated from [terraform-google-module-template](https://github.com/terraform-google-modules/terraform-google-module-template/), which by default generates a module that simply creates a GCS bucket. As the module develops, this README should be updated.

The resources/services/activations/deletions that this module will create/trigger are:

- Create a GCS bucket with the provided name

## Usage

Basic usage of this module is as follows:

```hcl
module "cloud_spanner" {
  source  = "terraform-google-modules/cloud-spanner/google"
  version = "~> 1.1"

  project_id  = "<PROJECT ID>"
  bucket_name = "gcs-test-bucket"
}
```

Functional examples are included in the
[examples](./examples/) directory.

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| backup\_schedule\_name | The name of the backup schedule | `string` | `"backup-schedule"` | no |
| cron\_spec\_text | The CRON spec text | `string` | `"0 2 * * *"` | no |
| database\_name | The name of the Spanner database | `string` | n/a | yes |
| instance\_name | The name of the Spanner instance | `string` | n/a | yes |
| project\_id | The project ID to deploy to | `string` | n/a | yes |
| retention\_duration | The duration for which the backup should be retained. | `string` | `"86400s"` | no |
| use\_full\_backup\_spec | Whether to use full backup specification. | `bool` | `true` | no |
| use\_incremental\_backup\_spec | Whether to use incremental backup specification. | `bool` | `false` | no |

## Outputs

| Name | Description |
|------|-------------|
| spanner\_schedule\_backup\_id | Spanner Schedule Backup ID |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Requirements

These sections describe requirements for using this module.

### Software

The following dependencies must be available:

- [Terraform][terraform] v0.13
- [Terraform Provider for GCP][terraform-provider-gcp] plugin v3.0

### Service Account

A service account with the following roles must be used to provision
the resources of this module:

- Storage Admin: `roles/storage.admin`

The [Project Factory module][project-factory-module] and the
[IAM module][iam-module] may be used in combination to provision a
service account with the necessary roles applied.

### APIs

A project with the following APIs enabled must be used to host the
resources of this module:

- Google Cloud Storage JSON API: `storage-api.googleapis.com`

The [Project Factory module][project-factory-module] can be used to
provision a project with the necessary APIs enabled.

## Contributing

Refer to the [contribution guidelines](./CONTRIBUTING.md) for
information on contributing to this module.

[iam-module]: https://registry.terraform.io/modules/terraform-google-modules/iam/google
[project-factory-module]: https://registry.terraform.io/modules/terraform-google-modules/project-factory/google
[terraform-provider-gcp]: https://www.terraform.io/docs/providers/google/index.html
[terraform]: https://www.terraform.io/downloads.html

## Security Disclosures

Please see our [security disclosure process](./SECURITY.md).
