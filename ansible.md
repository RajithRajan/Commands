Osboxes.org

Ansible
Ansible command is used to execute modules an ad-hoc basis without playbook
ansible all -m ping -i inventory.txt
ansible <host-patern> [-m module_name] [-a args] [option]
All is a group which ansible create which include all hosts defined in the inventory file.

Ansible-console similar to ansible

Ansible-pull
Inverts the default push architecture of ansible to pull architecture
ansible-pull -U <url> [options] [<filename.yml>]

Ansible-galaxy init
Ansible-galaxy init command is used to create a role from scratch. It creates folder structure required for the roles.
ansible-galaxy init <role-name>
Default location for roles /etc/ansible/roles/

Ansible-galaxy search
Search a role in ansible galaxy
ansible-galaxy search <search text>

Ansible-galaxy install
Install a role in the /etc/ansible/roles
ansible-galaxy install <role_name>

Ansible-playbook
Ansible-playbook is used to execute the playbook file
ansible-playbook ping-test.yaml -i inventory.txt

ping-test.yaml
-
  name: Test connectivity to all servers
  hosts: all
  task:
-  name: ping-test
    ping:

Ansible-vault
This is used to encrypt the password or inventory file it self
ansible-vault encrypt inventory.txt
ansible-vault view inventory.txt
ansible-playbook playbook.yml -i inventory.txt -ask-vault-pass
ansible-playbook playbook.yml -i inventory.txt -vault-password-file ~./vault_pass.txt/py

Ansible-doc
Display the documentation of the module
ansible-doc debug

Inventory keywords
ansible_host=<ip>/<host_name>
ansible_connection=ssh/winrm
ansible_user=<root/administrator>
ansible_ssh_pass=    (for linux and zOS)
ansible_password=   (for windows)

Grouping
[<group_name>]
host1
host2

Groups of group
[<parent_gr_name>: children]
group1
group2

Include
Include under task is used to include playbooks which needs to be executed this is used for creating reusable scripts which could be used by many playbook. These are stored under tasks directory

task:
-include: tasks\db_install.yml

Varible files
For defining invertory variables for a server
host_vars directory with yaml file with same name as server
group_vars directory with yaml file with same name as group

Modules
Apt/yum :- to install, uninstall and update application package
User - used for creation of new user
Service - used to start , stop and enable service
Command :- to issue any command to os
Shell :- to run command in a shell environment
MySQL :- to run command to create database
Mysql_user :- to create, delete and provide privilege
Pip :- to install python dependencies
Copy :- copy code to target location
File :- used for creation
Firewalld :- to enable and disable firewall for a service
Debug :- to display a msg
Windows Modules
win_command : used to run windows command
win_wait_for : used to wait for some text to appear in file
win_template : use Jinja template to create files
win-file : equivalent of file for windows
win_get_url : to download file from url
win_unzip :  to unzip a file
win_service: to start, stop and auto start windows service
win_shell:  to run power shell commands
win_path : to update path variable
win_environment: to set environment variable


Configuration for pipeline
Terraform init -input=false --backend-config=dev.conf

Terraform $tf_command -input=false -var-file=dev.tfvars -auto-approve
Custom modules
Documentation yml
Examples yml
Ansible_library environment variables to have custom module python directory
Ansible_filter_plugins environment variables should be set with path of filter py files
