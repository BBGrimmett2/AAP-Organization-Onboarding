# AAP Organization and Team Provisioning

This repository contains an Ansible playbook and supporting files to automate the provisioning of **organizations** and **teams** in **Ansible Automation Platform (AAP)**.

It uses templates and data files to generate AAP configuration and applies them via Ansible roles from supported collections.

---

<!-- ## Table of Contents

- [About](#about)  
- [Requirements](#requirements)  
- [Usage](#usage)  
- [Variables](#variables)  
- [File Structure](#file-structure)  
- [Collections](#collections)  
- [Contributing](#contributing)  
- [License](#license)

--- -->

## About

This project simplifies creation and management of organizational units and team structures in Ansible Automation Platform through a reusable Ansible playbook.

The intent is for this to be adaptable to different environments—modify templates and data as needed to match your AAP instance and naming conventions.

<!-- ---

## Requirements

Before running the playbook:

- **Ansible CLI installed** (2.16+ recommended)
- Valid environment variables for AAP API access:
  - `AAP_HOSTNAME`
  - `AAP_USERNAME`
  - `AAP_PASSWORD`
  - `AAP_VALIDATE_CERTS` *(optional — default set to false)*
- Organization input variables:
  - `organization_name`
  - `organization_full_name`
  - `organization_description` -->

---

## Usage

Invoke the provisioning playbook like this:

```yaml
ansible-playbook aap_org_team_provisioning.yml \
-e "org_name=my_org org_full_name='My Organization' org_description='Acme example description'"
```

---

## Variables

### Required

The following variables are required by the playbook. Most AAP connection values are sourced from environment variables.

| Variable | Description |
|--------|-------------|
| `aap_hostname` | Ansible Automation Platform hostname or URL. Sourced from `AAP_HOSTNAME`. |
| `aap_validate_certs` | Whether to validate SSL certificates when connecting to AAP. Defaults to `false`. |
| `aap_username` | AAP username used for API authentication. Sourced from `AAP_USERNAME`. |
| `aap_password` | AAP password used for API authentication. Sourced from `AAP_PASSWORD`. |
| `organization_name` | Short, unique identifier for the AAP organization. |
| `organization_full_name` | Human-readable display name for the organization. |
| `organization_description` | Description of the organization’s purpose. |
| `aap_authenticator` | Name of the configured AAP authenticator (e.g., LDAP / IdM). |
| `ad_group_name_admins` | Distinguished Name (DN) of the directory group mapped to organization admins. |
| `ad_group_name_users` | Distinguished Name (DN) of the directory group mapped to organization users. |

### Environment Variables

The following environment variables must be set before running the playbook:

```bash
export AAP_HOSTNAME=https://aap.example.com
export AAP_USERNAME=admin
export AAP_PASSWORD=changeme
export AAP_VALIDATE_CERTS=false
```


Additional variables (such as extra role mappings or team definitions) can be introduced by extending the playbook or survey.
