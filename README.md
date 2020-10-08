# Ansible learning notes
This is a ansible learning project that keeps all my notes and thoughts.

## Chapters
* 01_Installation
* 02_architecture_design
* 03_playbook
* 04_structuring_playbook
* playbook_examples

### Installation
* Install
  * *Installation for Linux Ubuntu*
```sudo apt-get upgrade
sudo apt-get install python-minimal virtualenv python-dev build-essential
mkdir ansible
cd ansible
virtualenv venv27
source venv27/bin/activate
pip install ansible
ansible --version
```

* Configure
  * ansible.cfg file
  * hosts file

### Useful commands
---
```#check syntax
ansible-playbook playbook.yml --check
ansible-playbook playbook.yml --syntax-check
ansible-playbook playbook.yml --step
#see the hosts that would be affected by your playbook 
ansible-playbook playbook.yml --list-hosts
#limit the hosts 
ansible-playbook playbook.yml --limit webserver
```

### TroubleShooting
---
* SSH login problem
  * On the server you cannot login, run a sshd service using different port:
`sudo /usr/sbin/sshd -d -p 1234`
Then go to ansible control server, try to connect to it
`ssh server_name -p 1234`
Go back to the server that you cannot login and try to find informations in the sshd log
*possible problem: the permission of authorized_keys is not 600*
* Log execution
```cat ansible.cfg
inventory = hosts
forks=5
log_path=/tmp/log.txt
```
* Ansible Verbosity
  * -v output data is displayed
  * -vv output and input data are displayed
  * -vvv additional information provided for connections to manage hosts
  * -vvvv extra verbosity that includes connection plugins and scripts etc




