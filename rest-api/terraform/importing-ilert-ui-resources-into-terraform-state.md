# Importing ilert UI resources into Terraform state

When working with with Terraform you have the option to create resources (managed by Terraform) or data sources (managed by ilert and read-only accessed by your Terraform config).

Often you have setup resources in ilert through API or UI before you start using Terraform to manage your setup and you want to know how to manage these resources as well, without deleting them first.

To do that, we can import resources into your local Terraform config.

**First step**: bring the configuration into your Terraform config

_Imagine we have the user Max Mustermann with the ID 123456 created through the UI in ilert_. To import him into TF, we first setup a block.

```hcl
 resource "ilert_user" "max_mustermann" {
  email              = "max.mustermann@gmail.com"
  first_name         = "Max"
  language           = "de"
  last_name          = "Mustermann"
  region             = "DE"
  role               = "USER"
  timezone           = "Europe/Berlin"
} 
```

{% hint style="info" %}
If you dont want to type the block by hand, you can also try to setup an import block for it and use the **-generate-config-out** argument ([https://developer.hashicorp.com/terraform/language/import/generating-configuration](https://developer.hashicorp.com/terraform/language/import/generating-configuration)) however we think that setting up the block by hand is faster.
{% endhint %}

**Second step**: now with the block setup, we need to tell Terraform to import the existing user from ilert into the block relation for the internal state management (otherwise TF will try to create a new user instead of updating it)

```
terraform import ilert_user.max_mustermann 123456
```

{% hint style="info" %}
Note that keys (identifiers) for the import might differ based on the resource (while in 99% it is the ID of the entity) you can find the import description at the bottom of each resource in the ilert Terraform provider's documentation.
{% endhint %}

After the import was successful, the block is now properly mapped to the identifer and you can continue as usual running `terraform plan` or `terraform apply`.
