---
layout: "rancher2"
page_title: "Rancher2: rancher2_project"
sidebar_current: "docs-rancher2-resource-project"
description: |-
  Provides a Rancher v2 Project resource. This can be used to create projects for rancher v2 environments and retrieve their information.
---

# rancher2\_project

Provides a Rancher v2 Project resource. This can be used to create projects for rancher v2 environments and retrieve their information.

## Example Usage

```hcl
# Create a new rancher2 Project
resource "rancher2_project" "foo" {
  name = "foo"
  cluster_id = "<CLUSTER_ID>"
  resource_quota {
    project_limit {
      limits_cpu = "2000m"
      limits_memory = "2000Mi"
      requests_storage = "2Gi"
    }
    namespace_default_limit {
      limits_cpu = "2000m"
      limits_memory = "500Mi"
      requests_storage = "1Gi"
    }
  }
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the project.
* `cluster_id` - (Required) The cluster id where create project.
* `description` - (Optional) A project description.
* `resource_quota` - (Optional) Resource quota for project. Rancher v2.1.x or higher 
* `annotations` - (Optional/Computed) Annotations for Node Pool object (map)
* `labels` - (Optional/Computed) Labels for Node Pool object (map)

### Project resource quota `resource_quota`

The following arguments are supported:

* `project_limit` - (Required) Resource quota limit for project.
* `namespace_default_limit` - (Required) Default resource quota limit for  namespaces in project

### Resource quota limit `project_limit` and `namespace_default_limit`

The following arguments are supported:

* `config_maps` - (Optional) Limit for config maps in project (string)
* `limits_cpu` - (Optional) Limit for limits cpu in project (string)
* `limits_memory` - (Optional) Limit for limits memory in project (string)
* `persistent_volume_claims` - (Optional) Limit for persistent volume claims in project (string)
* `pods` - (Optional) Limit for pods in project (string)
* `replication_controllers` - (Optional) Limit for replication controllers in project (string)
* `requests_cpu` - (Optional) Limit for requests cpu in project (string)
* `requests_memory` - (Optional) Limit for requests memory in project (string)
* `requests_storage` - (Optional) Limit for requests storage in project (string)
* `secrets` - (Optional) Limit for secrets in project (string)
* `services_load_balancers` - (Optional) Limit for services load balancers in project (string)
* `services_node_ports` - (Optional) Limit for services node ports in project (string)

More info at [resource-quotas](https://rancher.com/docs/rancher/v2.x/en/k8s-in-rancher/projects-and-namespaces/resource-quotas/)

## Attributes Reference

The following attributes are exported:

* `id` - (Computed) The ID of the resource.

## Import

Projects can be imported using the rancher Project ID

```
$ terraform import rancher2_project.foo <project_id>
```

