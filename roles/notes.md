################################################
### To run an Ansible playbook against a specific group of hosts defined in an inventory file, you can use the following command:

---
sidebar_position: Example
---

```
 ansible-playbook -i inv-expense expense-full.yml
```
```
ansible-playbook -i <inventory_file> <playbook_file> --limit <group_name>
```

Where:

* `-i` is the option to specify the inventory file
* `<inventory_file>` is the path to the inventory file
* `<playbook_file>` is the path to the playbook file
* `--limit` is the option to specify the group of hosts to target
* `<group_name>` is the name of the group of hosts to target

For example, to run the `expense-full.yml` playbook against the `expense` group of hosts defined in the `inv-expense` inventory file, you would use the following command:

```
ansible-playbook -i inv-expense expense-full.yml --limit expense
```

This command will execute the tasks defined in the `expense-full.yml` playbook on the hosts that are members of the `expense` group in the `inv-expense` inventory file. The results of the tasks will be displayed in the console.

Here is a breakdown of the command:

* `ansible-playbook`: This is the command to run an Ansible playbook.
* `-i inv-expense`: This specifies the inventory file to use, which in this case is `inv-expense`.
* `expense-full.yml`: This is the path to the playbook file to run.
* `--limit expense`: This specifies the group of hosts to target, which in this case is the `expense` group.

This command will ensure that the tasks defined in the playbook are only executed on the hosts that are relevant to the expense management process. This can help to improve the efficiency and reliability of your Ansible playbooks.

## Check Playbook and Inventory:

# The command ``` ansible-playbook -i inv-expense expense-full.yml``` is used to run an Ansible playbook named ``` expense-full.yml ``` against a set of hosts defined in an inventory file named ``` inv-expense ```

## Host Matching:
### Ensure that the hosts specified in your inventory file are correct and that the playbook's host patterns match the groups defined in the inventory.
################################################
### to run ansible playbook and inventory   command.

# ansible-playbook -i frontend.roboshop.internal, -e role_name=01.frontend expense.yml ; 

################################################..

