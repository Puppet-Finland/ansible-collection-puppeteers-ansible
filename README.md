# Ansible Collection - puppeteers.ansible

Documentation for the collection.

# Roles

## puppeteers.ansible.rulebook

This role manages ansible-runbook installations using Podman plus stuff on top
that may be required like firewalld. There is only one mandatory parameter:

* **puppeteers_ansible_rulebook_user_authorized_keys**: a list of SSH
authorized_keys for the "eda" user. This is required to use Podman commands
interactively.

If you wish to create a firewalld zone for ansible-rulebook you should set the
following parameters:

* **puppeteers_ansible_rulebook_manage_firewalld**: true
* **puppeteers_ansible_rulebook_firewalld_source**: an IP range you wish to allow access to ansible-rulebook from

There are several optional parameters available as well. Please refer to
[roles/rulebook/defaults/main.yml](roles/rulebook/defaults/main.yml) for
details.
