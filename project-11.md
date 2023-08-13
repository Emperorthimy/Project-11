## **Documentation for Project 11**

### Installing Ansible

`sudo apt update`

`sudo apt install ansible`

![Installing-Ansible](./Images/install-ansible.png)
![Installing-Ansible](./Images/ansible-version.png)

### Configuring Jenkins Build Job to save repository content anytime an Update is made

### Creating a Freestyle Project Ansible

![Freestyle-Project-Ansible](./Images/jenkins-config.png)

### Configuring Webhook to Trigger Ansible Build Automatically

![Webhook-Configuration](./Images/webhook.png)

### Configuring a Postbuild Job to Archive Artifacts

![Postbuild-Job-Configuration](./Images/Configuring-a-postbuild-job-to-archive-all-our-artifacts.png)

### Testing setup by Updating README File

### First Successful Build for Ansible

![1st-build-Success](./Images/build-1.png)

### Artifacts Saved Locally on Jenkins Server

![Artifacts-Saved-Locally](./Images/artifacts.png)

### Cloning Down ansible-config-mgt on ansible instance

`git clone https://github.com/Emperorthimy/ansible-config-mgt.git`

![Git-Clone](./Images/cloning.png)

![ansible-config-mgt-Clone](./Images/git-clone.png)

### Creating a new git Branch that will be used for the development of a new feature

![git-branch-created](./Images/git-new-branch.png)

### Checking out the newly created feature branch to our local machine to start building code and directory structure

### Setting up ssh host config

![ssh-host-config](./Images/ssh.png)

### Successful Connection to remote host Jenkins ansible server

![Connected-to-Jenkins-ansible-server](./Images/connect-to-jenkins-ansible-server.png)

### Checking out or switching to our newly created feature branch on our local machine

`git checkout -b feature/project-11-ansible`

![Successful-checkout-to-our-newly-created-feature-branch](./Images/branch-checkout.png)

![Successful-checkout-to-our-newly-created-feature-branch](./Images/git-branch.png)

### Creating files and folders for the development of our new features

![Files-and-folders-creation](./Images/Creating-our-files-and-folders-for-the-development-of-a-new-feature.png)

### Setting up our Ansible inventory in order to be able to ssh into remote host to execute tasks

### Importing our control server private key into ssh agent

#### Initializing SSH agent

`eval `ssh-agent -s` `

#### Path to our control server (Jenkins Ansible Server) Private Key

`ssh-add /home/ubuntu/.ssh/id_rsa`

![Importing-our-private-key-into-ssh-agent](./Images/ssh-agent.png)
![Importing-our-private-key-into-ssh-agent](./Images/ssh-keygen.png)

### Confirming our control server private key has been added to ssh agent

`ssh-add -l`

![Confirming-our-added-key](./Images/ssh-in-web1.png)

### SSH into webserver 1

`ssh -A ec2-user@3.133.146.195`

![ssh-into-webserver1-successful](./Images/ssh-webserver1.png)

### Updating our Inventory/dev.yml with the Private Ip's of the target servers

` [nfs] `
` 172.31.10.238 ansible_ssh_user='ec2-user' `

` [webservers] `
` 172.31.11.50 ansible_ssh_user='ec2-user' `
` 172.31.8.154 ansible_ssh_user='ec2-user' `

` [db] `
` 172.31.12.96 ansible_ssh_user='ubuntu' `

` [lb] `
` 172.31.36.27 ansible_ssh_user='ubuntu' `

![Updating-inventory-yml-with-target-servers-private-ip's](./Images/inventory-dev-yml.png)

### Testing Connectivity to one of our target servers in the inventory dev.yml file by Pinging Load Balancer(lb), returned success

`ansible lb -m ping -i dev.yml`

### Testing Connectivity to all of our target servers in the inventory dev.yml file by Pinging all, returned success

`ansible all -m ping -i dev.yml`

![connectivity-test-by-ping-to-all-of-our-target-servers-returned-success](./Images/test-ping-pong.png)

### Playing with ansible ad-hoc command

`ansible all -i dev.yml -m shell -a "df -h"`

![checking-my-mounts-on-webservers-using-ansible-adhoc-command-instead-of-ping](./Images/ad-hoc-commands.png)

`ansible all -i dev.yml -m shell -a "whoami"`

![checking-instance-type](./Images/more-ad-hoc.png)

### Testing our Playbook with wireshark Installation

#### Playbook file

`cat playbooks/common.yml`

![Playbook-file](./Images/common-yml.png)

#### Ansible-Playbook file test result

`ansible-playbook -i inventory/dev.yml playbooks/common.yml`

![Running-playbook-test](./Images/playbook-task.png)

#### Confirming our Ansible-playbook task execution on target servers

`which wireshark`
![wireshark-installation-success-via-control-server-on-target-servers](./Images/which-wireshark.png)

### Commiting our files to feature/project-11-ansible branch on Github via vs Code

`git status`

`git add .`

`git commit -m "adding our inventory and playbook files to our branch"`

![Commiting-our-files-to-github](./Images/git-status.png)

### Creating a Pull request (PR)

`git checkout main`

`git pull origin feature/project-11-ansible`

`git merge feature/project-11-ansible`

`git commit -m "Merge main into <your_branch>"`

`git push origin main`

![Creating-a-Pull-request](./Images/pull-request.png)

## Optional Steps taken to create directory and file on our Target Servers

`sudo cat common.yml`

![optional-step-playbook](./Images/dir-common-yml.png)

### Optional Steps

`ansible-playbook -i inventory/dev.yml playbooks/common.yml`

![optional-step-playbook-task](./Images/dir-playbook.png)

#### Optional Step Confirming our NodeJS Installation on target Servers

`ls /tmp`
![list-directory](./Images/result.png)
