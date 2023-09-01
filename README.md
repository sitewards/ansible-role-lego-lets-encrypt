# Ansible Lego (Let's Encrypt) Role

Ansible role for the Let's Encrypt client and ACME library [Lego](https://github.com/go-acme/lego)

## Design Notes

This role can be used to create any arbitrary number of certificates.
During deployment certificates are created only if thy do not exist, however
they are not renewed at this stage.  
Cron jobs for renewal are set up for all domains, this is the only mechanism of renewal in use.  

Currently, "dns" and "http" challenges are supported.


## Requirements
 - Ansible 2.10.0+
 - Python21
 - pip (installs dependencies if required)

## Usage

Add this role to your requirements file:

```
- src: "https://github.com/sitewards/ansible-role-lego-lets-encrypt"
  version: "3.0.0"
  name: "sitewards.lego-lets-encrypt"
```

alternatively you can clone this repo inside your roles folder:

```
    $ cd path/to/playbook/root
    $ mkdir roles/
    $ git clone https://github.com/sitewards/ansible-role-lego-lets-encrypt roles/sitewards.lego-lets-encrypt
``` 
   
Include this in another ansible playbook. For sample, consider a generic server playbook:

```
# $PLAYBOOK_ROOT/server.yaml

---
- name: "server"
  hosts: all
  become: true
  become_user: "root"
```

Add the reference for the role: 

```
# $PLAYBOOK_ROOT/server.yaml

# ...
become_user: "root"
roles
  - "sitewards.lets-encrypt"
```

## Limitations

Currently, this role does not provide mechanism of authentication against selected dns providers, this has to be handled externally
 
## Configuration
The variables that are available are defined in [defaults/main.yml](./defaults/main.yml). There are various requirements; 
check the file for further details.

##Contact

https://www.sitewards.com/
