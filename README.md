# DevOps (DaaS) - Configure Access
GitHub Actions : DevOps As A Service (DaaS) - Configure Access

![GitHub Actions - Configure Access](https://github.com/emvaldes/configure-access/workflows/GitHub%20Actions%20-%20Configure%20Access/badge.svg)

---
### GitHub Actions (Required):

[System Requirements](https://github.com/emvaldes/system-requirements) -
[Marketplace](https://github.com/marketplace/actions/system-requirements)
<br/>
[Generate Credentials](https://github.com/emvaldes/generate-credentials) - [Marketplace](https://github.com/marketplace/actions/generate-credentials)

---
### GitHub Variables (Required):

```console
UPDATE_SYSTEM              Updating Operating System (false)
UPGRADE_SYSTEM             Upgrading Operating System (false)

DEFAULT_TOOLS              Install packages from default list (default: null)
CUSTOM_TOOLS               Install packages from custom list (default: null)

UPDATE_PYTHON              Update Python to the latest version (true)
UPDATE_PIP                 Update Python package management (true)

PYTHON_REQUIREMENTS        Listing Python packages (default: null)

PRIVATE_KEYPAIR_FILE       Terraform AWS KeyPair (default: id_rsa)
PRIVATE_KEYPAIR_NAME       Terraform AWS KeyPair (e.g.: devops.pem)

AWSCLI_CLI                 Install Amazon WebServices CLI (false)
AWSCLI_DOWNLOAD            AWS CLI Download (awscli.amazonaws.com)
AWSCLI_PACKAGE             AWS CLI Package (e.g.: awscli-exe-linux-x86_64.zip)

VERBOSE_MODE               Identify verbosity level (false)
```
```console
TERRAFORM_CLI              Install Terraform CLI (false)
TERRAFORM_VERSION          Terraform specific target version (1.5.4)
```
```console
AWS_DEFAULT_PROFILE        The AWS Credentials Default User (e.g.: default).
AWS_DEFAULT_REGION         The AWS Default Region (e.g.: us-east-1)

DEVOPS_ACCESS_ROLE         Defines the AWS IAM Role: DevOps--Custom-Access.Role
DEVOPS_ACCOUNT_NAME        A Deployment Service Account name (devops).
```
---
### GitHub Secrets (Required):

```console
AWS_ACCESS_KEY_ID          Service-Account AWS Access Key-Id (e.g.: AKIA2...VT7DU).
AWS_DEFAULT_ACCOUNT        The AWS Account number (e.g.: 123456789012).
AWS_SECRET_ACCESS_KEY      Service-Account AWS Secret Access Key (e.g.: zBqDUNyQ0G...IbVyamSCpe)

PRIVATE_KEYPAIR_SECRET     Terraform AWS KeyPair (PEM, Private file)
```
