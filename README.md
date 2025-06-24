New user create and sudo permission automation on ubuntu
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## How to run this role

### Create playbook.yml in control host
Example yaml file: 

```bash
---
- hosts: all
  become: true
  roles:
    - waseralkarim.sudouser
```
### Create inventory file
Example inventory file:

```bash
[all]
<remote_server_ip> ansible_user=ubuntu
```

### Generate SSH Key on Your Control Node (if not already)

If you haven't already done this on your Ansible **control machine (your Ubuntu system)**:

```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_rsa

```

(Press Enter at prompts to accept defaults)

This creates:

- `~/.ssh/id_rsa` (private key)
- `~/.ssh/id_rsa.pub` (public key)

---

### Copy Your SSH Public Key to the Target Host

To avoid `--ask-pass` every time and use SSH key authentication:

```bash
ssh-copy-id ubuntu@<remote_server_ip>

```

Run command:

```bash
ansible-playbook -i inventory playbook.yml
```


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
