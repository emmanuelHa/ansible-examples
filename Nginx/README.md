# Ansible
This project is an example of how to install Nginx to a Debian or a Fedora machine (ansible_host) and customize it accordingly with ansible.  
## Installation:

```sh
sudo apt update
sudo apt install ansible
ansible --version
```

<!---
{::comment}  
# kubectl run flow-pod -i --tty --image debian:bullseye # --restart=Never -- bash
{:/comment}
--->

## How to use ?  

To contact the debian machine from a local machine with ansible installed on it and inventory 'hosts' and group named 'web':
```sh
> sudo apt-get install sshpass
> ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory/hosts web -m ping 
```
Run the playbook on the remote machine replacing host ip and user passord accordlingly: 
```sh
 ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i inventory/hosts.yml playbook.yml --extra-vars="env=staging ansible_host=x.x.x.x ansible_ssh_user=admin ansible_ssh_pass=xxxxxx"
```

**Examples of commands (group is named 'web' here for inventory 'hosts'):** 
```sh
> ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory/hosts web -a "hostname -f"

> ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory/hosts web -m copy -a "src=hello.txt dest=/home/admin/hello.txt"
> ANSIBLE_HOST_KEY_CHECKING=False ansible -i inventory/hosts web -a "cat /home/admin/hello.txt"
```

Example of inventories: 
https://linux.goffinet.org/ansible/comprendre-inventaire-ansible/