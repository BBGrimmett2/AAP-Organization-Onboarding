# AAP Organization and Team Provisioning

## Overview
This Ansible playbook automates the provisioning of organizations and teams in **Ansible Automation Platform (AAP)**. It generates configuration files from templates, appends data to tracking files, and applies configurations using predefined roles.

## Requirements
- Ansible installed
- Required environment variables:
  - `AAP_HOSTNAME`
  - `AAP_VALIDATE_CERTS` (optional, defaults to `false`)
  - `AAP_USERNAME`
  - `AAP_PASSWORD`
- Organization variables must be defined:
  - `org_name`
  - `org_full_name`
  - `org_description`
- Collections Requirements
```yaml
---
collections:
# VALIDATED RED HAT CONTENT
  - name: ansible.platform
  - name: ansible.hub
  - name: ansible.controller
  - name: ansible.eda
  - name: infra.aap_configuration
```
## Usage
Run the playbook with:

```sh
ansible-playbook aap_org_team_provisioning.yml -e "org_name=my_org org_full_name='My Organization' org_description='Description here'"
```

## File Structure
```sh
├── aap_org_team_provisioning.yml  # Playbook file
├── templates/
│   ├── organization.yml.j2        # Organization template
│   ├── team.yml.j2                # Team template
├── data/
│   ├── aap_organizations.yml      # Organization tracking file
│   ├── aap_teams.yml              # Team tracking file
```
