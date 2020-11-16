---
description: >-
  The iLert Terraform Integration helps you to easily create and manage iLert
  resources.
---

# HashiCorp Terraform

You can find the official iLert Terraform Provider documentation [here](https://registry.terraform.io/providers/iLert/ilert/latest/docs) and [the source code for it](https://github.com/iLert/terraform-provider-ilert) on our Github organization.

```text
provider "ilert" {
    organization = "your organization"
    username     = "your username"
    password     = "password"
}

data "ilert_escalation_policy" "default" {
  name = "Default"
}

resource "ilert_alert_source" "example" {
  name                    = "My Grafana Integration"
  integration_type        = "GRAFANA"
  escalation_policy       = data.ilert_escalation_policy.default.id
  incident_priority_rule  = "HIGH_DURING_SUPPORT_HOURS"

  support_hours {
    timezone = "Europe/Berlin"

    support_days {
      monday {
        start = "08:00"
        end   = "17:00"
      }

      tuesday {
        start = "08:00"
        end   = "17:00"
      }

      wednesday {
        start = "08:00"
        end   = "17:00"
      }

      thursday {
        start = "08:00"
        end   = "17:00"
      }

      friday {
        start = "08:00"
        end   = "17:00"
      }
    }
  }
}
```

Please feel free to reach out to us with a Github issue in case you need help or have feature requests.

