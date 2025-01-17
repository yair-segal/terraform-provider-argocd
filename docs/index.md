---
page_title: "Provider: ArgoCD"
description: |-
  The ArgoCD provider provides lifecycle management of ArgoCD resources.
---

# ArgoCD Provider

The ArgoCD Provider provides lifecycle management of
[ArgoCD](https://argo-cd.readthedocs.io/en/stable/) resources.

**NB**: The provider is not concerned with the installation/configuration of
ArgoCD itself. To make use of the provider, you will need to have an existing
ArgoCD installation and, the ArgoCD API server must be
[accessible](https://argo-cd.readthedocs.io/en/stable/getting_started/#3-access-the-argo-cd-api-server)
from where you are running Terraform.

## Example Usage

```terraform
provider "argocd" {
  server_addr = "argocd.local:443"
  auth_token  = "1234..."
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- `auth_token` (String) ArgoCD authentication token, takes precedence over `username`/`password`. Can be set through the `ARGOCD_AUTH_TOKEN` environment variable.
- `cert_file` (String) Additional root CA certificates file to add to the client TLS connection pool.
- `client_cert_file` (String) Client certificate.
- `client_cert_key` (String) Client certificate key.
- `config_path` (String) Override the default config path of `$HOME/.config/argocd/config`. Only relevant when `use_local_config`. Can be set through the `ARGOCD_CONFIG_PATH` environment variable.
- `context` (String) Kubernetes context to load from an existing `.kube/config` file. Can be set through `ARGOCD_CONTEXT` environment variable.
- `grpc_web` (Boolean) Whether to use gRPC web proxy client. Useful if Argo CD server is behind proxy which does not support HTTP2.
- `grpc_web_root_path` (String) Use the gRPC web proxy client and set the web root, e.g. `argo-cd`. Useful if the Argo CD server is behind a proxy at a non-root path.
- `headers` (Set of String) Additional headers to add to each request to the ArgoCD server.
- `insecure` (Boolean) Whether to skip TLS server certificate. Can be set through the `ARGOCD_INSECURE` environment variable.
- `kubernetes` (Block List, Max: 1) Kubernetes configuration. (see [below for nested schema](#nestedblock--kubernetes))
- `password` (String) Authentication password. Can be set through the `ARGOCD_AUTH_PASSWORD` environment variable.
- `plain_text` (Boolean) Whether to initiate an unencrypted connection to ArgoCD server.
- `port_forward` (Boolean)
- `port_forward_with_namespace` (String)
- `server_addr` (String) ArgoCD server address with port. Can be set through the `ARGOCD_SERVER` environment variable.
- `use_local_config` (Boolean) Use the authentication settings found in the local config file. Useful when you have previously logged in using SSO. Conflicts with `auth_token`, `username` and `password`.
- `user_agent` (String)
- `username` (String) Authentication username. Can be set through the `ARGOCD_AUTH_USERNAME` environment variable.

<a id="nestedblock--kubernetes"></a>
### Nested Schema for `kubernetes`

Optional:

- `client_certificate` (String) PEM-encoded client certificate for TLS authentication. Can be sourced from `KUBE_CLIENT_CERT_DATA`.
- `client_key` (String) PEM-encoded client certificate key for TLS authentication. Can be sourced from `KUBE_CLIENT_KEY_DATA`.
- `cluster_ca_certificate` (String) PEM-encoded root certificates bundle for TLS authentication. Can be sourced from `KUBE_CLUSTER_CA_CERT_DATA`.
- `config_context` (String) Context to choose from the config file. Can be sourced from `KUBE_CTX`.
- `config_context_auth_info` (String)
- `config_context_cluster` (String)
- `config_path` (String) Path to the kube config file. Can be sourced from `KUBE_CONFIG_PATH`.
- `config_paths` (List of String) A list of paths to the kube config files. Can be sourced from `KUBE_CONFIG_PATHS`.
- `exec` (Block List, Max: 1) Configuration block to use an [exec-based credential plugin](https://kubernetes.io/docs/reference/access-authn-authz/authentication/#client-go-credential-plugins), e.g. call an external command to receive user credentials. (see [below for nested schema](#nestedblock--kubernetes--exec))
- `host` (String) The hostname (in form of URI) of the Kubernetes API. Can be sourced from `KUBE_HOST`.
- `insecure` (Boolean) Whether server should be accessed without verifying the TLS certificate. Can be sourced from `KUBE_INSECURE`.
- `password` (String) The password to use for HTTP basic authentication when accessing the Kubernetes API. Can be sourced from `KUBE_PASSWORD`.
- `token` (String) Token to authenticate an service account. Can be sourced from `KUBE_TOKEN`.
- `username` (String) The username to use for HTTP basic authentication when accessing the Kubernetes API. Can be sourced from `KUBE_USER`.

<a id="nestedblock--kubernetes--exec"></a>
### Nested Schema for `kubernetes.exec`

Required:

- `api_version` (String) API version to use when decoding the ExecCredentials resource, e.g. `client.authentication.k8s.io/v1beta1`.
- `command` (String) Command to execute.

Optional:

- `args` (List of String) Map of environment variables to set when executing the plugin.
- `env` (Map of String) List of arguments to pass when executing the plugin.