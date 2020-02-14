ANSIBLE-ROLE-BASHALIASES
========================

Ansible role add Bash aliases in bash file you want.


## Howto use this role?
This role need to be include in a playbook. 

Call this **Galaxy** role  like this:

````bash
ansible-galaxy install -r requirements.yml 
````

Inside requirements.yml
````yaml
# from GitHub, overriding the name and specifying a specific tag
- src: redbeard28.bashaliases
````

More info => [Ansible Docs](https://docs.ansible.com/ansible-container/roles/access.html)

## Requirements

 * Ansible 2.9+


Role Variables
--------------

```yaml
---
activate_shell_aliases_extra: false
aliases_shell: "bash"
shell_rc_file: "~/.{{ aliases_shell }}rc"
shell_aliases_file: "~/.{{ aliases_shell }}_aliases"

shell_aliases:
  - {alias: "ll", command: "ls -rthl --color=auto"}
  - {alias: "dir", command: "dir --color=auto"}
  - {alias: "grep", command: "grep --color=auto"}

shell_aliases_extra:
  - \#function inspec { docker run -it --rm -v $(pwd):/share -v $(echo $HOME):/home/ chef/inspec "$@"; }
  - export cookiecutterURL=https://github.com/redbeard28/ansible-role-template.git

```

Dependencies
------------

**if python3 is not installed on remote host**

- src: redbeard28.bootstrap 

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - { role: redbeard28.bashaliases, tags: mytags }


Molecule testing framework
--------------------------

You can use molecule to test this role.
```bash
image=debian tag="buster" molecule converge 
image=debian tag="buster" molecule verify 
```

Author Information
------------------

Jeremie CUADRADO[¹](mailto:info@redbeard-consulting.fr) from Redbeard-Consulting
