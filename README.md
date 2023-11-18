```
- name: My Playbook
  hosts: target_hosts
  become: yes          # Run tasks with elevated privileges
  roles:
    - my_role

```
>>> role: inside this data structure will use the following roles:

```
roles/
|-- my_role/
|   |-- tasks/
|   |   └-- main.yml
|   |-- handlers/
|   |   └-- main.yml
|   |-- templates/
|   |-- files/
|   |-- vars/
|   |   └-- main.yml
|   |-- defaults/
|   |   └-- main.yml
|   |-- meta/
|       └-- main.yml
```
> Roles are included in Ansible playbooks using the roles keyword. For example:



