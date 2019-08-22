Ansible-root-passchanger
=========

Playbook for change root passwords on linux system. 
If you run random pass it would be saved in /root/root_pass_base.txt
Also, if you forgot your new password, you can copy your old shadow password from /etc/shadow.old to /etc/shadow

Requirements
------------

Any linux system

Role Variables
--------------
You can change password randomizer command and password salt in ./global_vars/all

random_pass:
root_password_salt: 

Example Playbook
----------------

```
- hosts: rootpasschange
  become: yes
  gather_facts: no
  vars_prompt:
  - name: "new_pass"
    prompt: Type in new password
    private: yes
    confirm: yes
  vars:
    root_password_salt: afEMnMOBZgYNhoqAcdaSFJkikafiuSlk
  roles:
  - role: passchanger
```  

```
- name: passchanger_random
  hosts: rootpasschange
  become: yes
  vars_prompt:
  - name: "user"
    prompt: Type USER to change password
    private: no
  roles: 
  - role: passchanger_random
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
