[![MIT License](https://raw.githubusercontent.com/DO1JLR/ansible_playbook_template/main/.github/license.svg?sanitize=true)](https://github.com/DO1JLR/ansible_playbook_template/blob/main/LICENSE)

 Ansible Playbook to set up some of my servers
=========================================

This is a ansible playbook to setup some of my Servers.
Including webserver for some of my domains and my mailserver.

+ For more general Information have a look in the ``docs/`` Folder.
+ For a highly exact information and when you have a deeper understanding of ansible use the ``site.yml`` to understand which roles we are putting together. We tried to store all non sensible used variables in the unencrypted vars.yml.

 Tipps und Tricks:
---------
### git submodule
Dieses Ansible verwendet submodule. Vergesst nicht diese regelmäßig mit auszuchecken!
```
git config submodule.recurse true
git submodule update --init --recursive
```

### Standard Playbook
Das standard Playook ist ``site.yml``. Womöglich sind hier andere Playbooks eingebunden...

### best practise Ansible-Vault:
