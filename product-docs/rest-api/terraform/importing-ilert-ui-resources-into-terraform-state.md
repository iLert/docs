# Importing ilert UI resources into Terraform state

When working with with Terraform you have the option to create resources (managed by Terraform) or data sources (managed by ilert and read-only accessed by your Terraform config).

Often you have setup resources in ilert through API or UI before you start using Terraform to manage your setup and you want to know how to manage these resources as well, without deleting them first.

To do that, we can import resources into your local Terraform config.

## **First step**: Block&#x20;

Bring the configuration into your Terraform config.

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

## **Second step**: Import

Now with the block setup, we need to tell Terraform to import the existing user from ilert into the block relation for the internal state management (otherwise TF will try to create a new user instead of updating it)

```
terraform import ilert_user.max_mustermann 123456
```

{% hint style="info" %}
Note that while in 99% of the cases, the import keys (identifiers) are the same as the entity’s ID, they sometimes might differ. You can find the import description at the bottom of each resource in [the ilert Terraform provider’s documentation](https://registry.terraform.io/providers/iLert/ilert/latest).
{% endhint %}

After the import was successful, the block is now properly mapped to the identifer and you can continue as usual running `terraform plan` or `terraform apply`.



## FAQ

### **How to figure out the ID of my resource?**

You can either use the API or the UI to find the identifier of your resource:

**In the UI** head to the detail view of your desired resource and copy the id param of your browser's URL:

<figure><img src="../../.gitbook/assets/image (229).png" alt=""><figcaption></figcaption></figure>

**For the API**, you may call the GET list resources of your entities e.g. `GET /api/alert-sources` and use the **id** field of the returned objects.

<figure><img src="../../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure>

Should you have many entities, we recommend using the _(inofficial)_ `?query=` param to search for the name of your desired resource:

<figure><img src="../../.gitbook/assets/image (231).png" alt=""><figcaption></figcaption></figure>
