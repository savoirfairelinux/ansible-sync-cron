# ansible-sync-cron

*Provisions crontab entries allowing to rsync folders, SFL style.*

## Requirements

* Ansible 2.0+
* Debian Jessie on the target system
* A provisioning that runs [ansible-common][ansible-common] before this.

## Usage

You call this role as with any other roles. See [vars file](defaults/main.yml) for customisation
options.

Here's an example usage for a local development environment:

```yaml
---
- name: Install a cronjob allowing to synchronize backups
  hosts: sync-cron-test

  roles:
    - role: sync_cron
      sync_cron_username: "user"
      sync_cron_src_path: "user@testdomain.net:*"
      sync_cron_dest_url: "/backups/test"
      sync_cron_freq:
        name: "backup cron for test"
        hour: 3
        minute: 10

```


[ansible-common]: https://gitlab.savoirfairelinux.com/devops/ansible-common
