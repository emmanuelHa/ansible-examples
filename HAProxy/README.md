# Ansible
This project is an example of how to install Nginx to 2 servers (ansible_host1, ansible_host2) with an HAProxy (ansible_host3) in front with ansible.  
## Local installation of ansible:

```sh
sudo apt update
sudo apt install ansible
ansible --version
```

## How to use ?  

To contact the debian machine from a machine with ansible installed on it:
```sh
> sudo apt-get install sshpass
```
Run the playbook on the remote machine replacing host ip and user password accordlingly: 
```sh
ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i inventory/hosts.yml playbook.yml --extra-vars="ansible_host1=x.x.x.x ansible_host2=y.y.y.y ansible_host3=z.z.z.Z ansible_user=admin ansible_ssh_pass=xxxxxxxx"
```