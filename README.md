
Vagrant CI
Using a configuration management language of your choosing (Ansible, Puppet, Salt, Chef) setup a 
Continuous Integration server of your choosing on a Vagrant Box. You are not required to setup Vagrant or 
its requirements on the host machine.

Pre-requisite softwares  : Python 3.6.8,ansible 2.9.27
Assumption : Above softwares already installed on vagrant box

steps to follow to complete exercise

ssh to vagrant box

ssh-keygen
ssh-copy-id -i localhost

mkdir -p /home/vagrant/roles

vi inventory

[dev]
localhost

cp /etc/ansible/ansible.cfg /home/vagrant/ansible

vi ansible.cfg
Inventory =/home/vagrant/ansible/inventory

become=True
become_method=sudo
become_user=root

roles_path=/home/vagrant/ansible/roles 
host_key_checking=False



export ANSIBLE_CONFIG=/home/vagrant/ansible/ansible.cfg

vi .bash_profile
export ANSIBLE_CONFIG=/home/vagrant/ansible/ansible.cfg


$ ansible --version
$ ansible all -m ping


Install roles using Ansible Galaxy
ansible-galaxy init jenkins

roles/jenkins/tasks/main.yaml

create yaml file to call jenkins role



ansible-playbook --syntax-check jenkins.yaml

ansible-playbook -C jenkins.yaml

ansible-playbook jenkins.yaml

check jenkins is installed by running

ansible dev -m shell -a 'rpm -qa |grep jenkins'

check port listening -- netstat -tulpn |grep 8080

Login to jenkins with password appeared from console..

