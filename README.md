# Ansible Training
Quickstart: Clone this stack to quickly deploy your cluster (1 ansible + 1 client) 
  > git clone https://github.com/Matsiaze/cursus-devops.git
  >  // Go to : cursus-devops/vagrant/ansible/ to run *vagrant up*

## 1. In the repo **docker** 
- Install docker and pip immediately on your client
  > Play install-docker.yml in the repository *docker/*:
  > *ansible-playbook -i hosts install-docker.yml* 

## 2. In the repo **webapp**:
- Experiment Ad Hoc Command
  > ansible -i hosts all -m ping
  > // ansible -i hosts all -m setup
  > // ansible -i hosts.ini all -m copy -a "dest=/home/vagrant/{{ env }} content='hello from ansible {{ env }} environment'"

And more: https://github.com/Matsiaze/ansible-modules-core.git

- Experiment playbook to deploy apache on your client
  > Go to *webapp/* and play one *deploy.yml* book:  
  > *ansible-playbook -i prod.yml deploy2.yml*

- Install docker and pip immediately on your client
  > Play install-docker.yml in the repository *webapp/docker*: 
  > *ansible-playbook -i hosts install-docker.yml*

## 3. In the repo **webapp2**:

Deploy a welcome website on the client host
- Experiment templates
  > Implement a template index.html.j2
- Experiment conditional loops
  > Use a loop to implement some packages on specific OS
- Experiment volume mount
  > Mount the file index.html in the default location for httpd image
- Deploy your website
  > Play your book and deploy your site using apache...Check your client host
- Refer on documentation:
  > https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_loops.html // https://hub.docker.com/_/httpd // https://docs.ansible.com/ansible/latest/collections/ansible/builtin/template_module.html

## 4. In the repo **webapp_secure**

Enhance good practices using vault for credentials and sensitive datas

- Encapsulate credentials
  > Use file *files/secrets/credentials.vault*
- Encrypt using ansible vault
  > ansible-vault encrypt credentials.vault //
  > Set the vars_file in your *deploy.yml* playbook
- Deploy your site
  >  *ansible-playbook -i prod.yml --ask-vault-pass deploy.yml* //
- Go further and configure access through ssh: Generate key pair and pass the .pub to client
  > *ssh-keygen - t rsa*  and *ssh-copy-id vagrant@hostip*

## 5. In the repo **wordpress**

Develop maintanability using **roles**
- Use ansible galaxy as ref documentation
  > https://galaxy.ansible.com/home //
  > Use a containerized wordpress role template in: https://github.com/diranetafen/ansible-role-containerized-wordpress.git // ansible-galaxy install -r roles/requirements.yml
- Deploy wordpress using docker and ansible roles
