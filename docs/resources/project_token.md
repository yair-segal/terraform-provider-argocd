---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "argocd_project_token Resource - terraform-provider-argocd"
subcategory: ""
description: |-
  Manages ArgoCD project role JWT tokens. See Project Roles https://argo-cd.readthedocs.io/en/stable/user-guide/projects/#project-roles for more info.
---

# argocd_project_token (Resource)

Manages ArgoCD project role JWT tokens. See [Project Roles](https://argo-cd.readthedocs.io/en/stable/user-guide/projects/#project-roles) for more info.

~> **Security Notice** The JWT token generated by this resource is treated as
sensitive and, thus, not displayed in console output. However, it will be stored
*unencrypted* in your Terraform state file. Read more about sensitive data
handling in the [Terraform
documentation](https://www.terraform.io/docs/language/state/sensitive-data.html).


## Example Usage

```terraform
resource "argocd_project_token" "secret" {
  project      = "someproject"
  role         = "foobar"
  description  = "short lived token"
  expires_in   = "1h"
  renew_before = "30m"
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `project` (String) The project associated with the token.
- `role` (String) The name of the role in the project associated with the token.

### Optional

- `description` (String) Description of the token.
- `expires_in` (String) Duration before the token will expire. Valid time units are `ns`, `us` (or `µs`), `ms`, `s`, `m`, `h`. E.g. `12h`, `7d`. Default: No expiration.
- `renew_before` (String) Duration to control token silent regeneration, valid time units are `ns`, `us` (or `µs`), `ms`, `s`, `m`, `h`. If `expires_in` is set, Terraform will regenerate the token if `expires_in - renew_before < currentDate`.

### Read-Only

- `expires_at` (String) If `expires_in` is set, Unix timestamp upon which the token will expire.
- `id` (String) The ID of this resource.
- `issued_at` (String) Unix timestamp at which the token was issued.
- `jwt` (String, Sensitive) The raw JWT.


