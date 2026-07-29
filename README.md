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

## puppeteers.ansible.rulebook_target

This role enables SSH access from ansible-rulebook, or rather, ansible runner
launched by it. It creates a dedicated system user and puts one or more
authorized SSH keys into ~/.ssh/authorized_keys with optional key options (e.g.
from="10.0.0.1"). Limiting privileges for the user beyond group membership is
outside of the scope of this role. This role has three paramaters:

    **puppeteers_ansible_rulebook_target_user_authorized_keys**: list of authorized SSH keys to allow access with (mandatory, see usage below)
    **puppeteers_ansible_rulebook_target_user**: name of the system user to create (optional, default: *eda*)
    **puppeteers_ansible_rulebook_target_user_groups**: list of additional groups to add the user to (optional, default: [])

The *puppeteers_ansible_rulebook_target_user_authorized_keys* parameter expects
the following format:

    puppeteers_ansible_rulebook_target_user_authorized_keys:
      - key: "key-type first-key-content comment"
        key_options: ""
      - key: "key-type second-key-content comment"
        key_options: "from=\"10.0.0.5\""
