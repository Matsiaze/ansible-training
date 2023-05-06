# Ansible Training
Quickstart: Clone this stack to quickly deploy your cluster (1 ansible + 1 client) https://github.com/Matsiaze/cursus-devops.git
Go to : cursus-devops/vagrant/ansible/ to run vagrant up

# 1. Experiment Ad Hoc Command
ansible -i hosts all -m ping
ansible -i hosts all -m setup
ansible -i hosts.ini all -m copy -a "dest=/home/vagrant/{{ env }} content='hello from ansible {{ env }} environment'"
And more... https://github.com/Matsiaze/ansible-modules-core.git

# 2. Deploy apache on your client
Experiment playbook: go to webapp and play

# 3. To Install docker on your client
Play install-docker.yml in the repository docker 
ansible-playbook -i hosts install-docker.yml

