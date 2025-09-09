# Datadog GCP integration module

Terraform module which creates Datadog GCP integration and service account resources on GCP.

## Usage

### Create Artifact Registry

```hcl
module "datadog_gcp_integration" {
  source  = "c0x12c/gcp-integration/datadog"
  version = "~> 1.1.0"

  datadog_account_id   = "datadog"
}
```

## Examples

- [Example](./examples/complete/)

<!-- BEGIN_TF_DOCS -->

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.9.8 |
| <a name="requirement_datadog"></a> [datadog](#requirement\_datadog) | >= 3.46 |
| <a name="requirement_google"></a> [google](#requirement\_google) | >= 6.12 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_datadog"></a> [datadog](#provider\_datadog) | 3.67.0 |
| <a name="provider_google"></a> [google](#provider\_google) | 6.43.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_service_account"></a> [service\_account](#module\_service\_account) | c0x12c/service-account/gcp | 1.0.0 |

## Resources

| Name | Type |
|------|------|
| [datadog_integration_gcp_sts.this](https://registry.terraform.io/providers/DataDog/datadog/latest/docs/resources/integration_gcp_sts) | resource |
| [google_service_account_iam_member.this](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/service_account_iam_member) | resource |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_automute"></a> [automute](#input\_automute) | Determines whether to automatically mute monitors related to this integration during a downtime. Set to 'true' to enable automatic muting and 'false' to disable it. | `bool` | `true` | no |
| <a name="input_datadog_account_id"></a> [datadog\_account\_id](#input\_datadog\_account\_id) | The datadog account name to create. | `string` | n/a | yes |
| <a name="input_datadog_roles"></a> [datadog\_roles](#input\_datadog\_roles) | Datadog service account should have compute.viewer, monitoring.viewer, cloudasset.viewer, and browser roles (the browser role is only required in the default project of the service account). | `list(string)` | <pre>[<br/>  "roles/compute.viewer",<br/>  "roles/container.viewer",<br/>  "roles/monitoring.viewer",<br/>  "roles/cloudasset.viewer",<br/>  "roles/browser"<br/>]</pre> | no |
| <a name="input_gcp_services_enabled"></a> [gcp\_services\_enabled](#input\_gcp\_services\_enabled) | Values to enable GCP services in Datadog integration. | <pre>list(object({<br/>    id       = string<br/>    disabled = bool<br/>  }))</pre> | <pre>[<br/>  {<br/>    "disabled": true,<br/>    "id": "actions"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "aiplatform"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "alloydb"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "apigateway"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "apigee"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "appengine"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "apphub"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "artifactregistry"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "autoscaler"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "backupdr"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "baremetalsolution"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "bigquery"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "bigquerybiengine"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "bigquerydatatransfer"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "bigquerystorage"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "bigtable"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "billingbudgets"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "blockchainnodeengine"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "certificatemanager"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "chronicle"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "clouddeploy"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "cloudfunctions"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "cloudkms"<br/>  },<br/>  {<br/>    "disabled": false,<br/>    "id": "cloudsql"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "cloudtasks"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "cloudtrace"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "composer"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "compute"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "connectors"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "contactcenterinsights"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "container"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "custom"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "dataflow"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "datamigration"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "dataplex"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "dataproc"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "datastore"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "datastream"<br/>  },<br/>  {<br/>    "disabled": false,<br/>    "id": "dbinsights"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "dialogflow"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "displayvideo"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "dlp"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "dns"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "earthengine"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "edgecache"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "edgecontainer"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "external"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "file"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firebaseappcheck"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firebaseauth"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firebasedatabase"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firebasedataconnect"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firebaseextensions"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firebasehosting"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firebasestorage"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firestore"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "firewallinsights"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "fleetengine"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "gkebackup"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "healthcare"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "iam"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "identitytoolkit"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "ids"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "integrations"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "interconnect"<br/>  },<br/>  {<br/>    "disabled": false,<br/>    "id": "kubernetes"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "livestream"<br/>  },<br/>  {<br/>    "disabled": false,<br/>    "id": "loadbalancing"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "logging"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "managedflink"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "managedidentities"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "managedkafka"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "maps"<br/>  },<br/>  {<br/>    "disabled": false,<br/>    "id": "memcache"<br/>  },<br/>  {<br/>    "disabled": false,<br/>    "id": "memorystore"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "metastore"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "ml"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "monitoring"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "netapp"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "networkconnectivity"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "networking"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "networksecurity"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "networkservices"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "oracledatabase"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "osconfig"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "parallelstore"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "privateca"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "prometheus"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "pubsub"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "pubsublite"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "recaptchaenterprise"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "recommendationengine"<br/>  },<br/>  {<br/>    "disabled": false,<br/>    "id": "redis"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "retail"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "router"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "run"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "serviceruntime"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "spanner"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "storage"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "storagetransfer"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "telcoautomation"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "tpu"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "trafficdirector"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "transferappliance"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "translationhub"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "videostitcher"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "visionai"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "vpcaccess"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "vpn"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "workflows"<br/>  },<br/>  {<br/>    "disabled": true,<br/>    "id": "workload"<br/>  }<br/>]</pre> | no |
| <a name="input_host_filters"></a> [host\_filters](#input\_host\_filters) | A string used to filter the hosts sent from GCP to Datadog. Only hosts matching the specified tags will be included. Tags should be in the format 'key:value' and multiple tags can be separated by commas (e.g., 'environment:production,datadog:true'). | `string` | `"datadog:true"` | no |
| <a name="input_is_cspm_enabled"></a> [is\_cspm\_enabled](#input\_is\_cspm\_enabled) | Indicates whether CSPM (Cloud Security Posture Management) is enabled in the Terraform configuration. Disable to save cost. | `bool` | `false` | no |

## Outputs

No outputs.

<!-- END_TF_DOCS -->
