# ansible_basic
It's projest how to start useing [Ansible](https://www.ansible.com) - Dependency Management. Installing "Ansible server" and start in simple way IT automation.

## Prerequisites

Two virtual machine witch linux Centos (vbox, vagrant, ..).
Host for Ansible it can be our laptop or another virtual machine. 
All virtual machines and Ansible host must be in the same network.

## Prepare environment

### Ansible/Server
1. Install Centos7
2. Install Ansible
- sudo yum install epel-release
- sudo yum install ansible
3. Install git
- yum install git
4. Clone repository
5. Generate ssh *.pub key
- ssh-keygen -f ansiblekey
6. Move your generated keys to ~/.ssh/ directory
- mv ansiblekey ~/.ssh/
- mv ansiblekey.pub ~/.ssh/

7.Add private key identities to the authentication agent
- ssh-add ~/.ssh/ansiblekey

### Hosts

1. Create two or more Centos hosts.
2. On each host:
- Create user ansible
  - adduser ansible
  - passwd ansible
- Edit the sudores file and and sudo no password for ansible user
  - visudo - and add line "ansible         ALL=(ALL)       NOPASSWD: ALL"
3. Copy ~/.ssh/ansiblekey.pub from ansible server to all hosts (remember to change IP address)
- ssh-copy-id -i ~/.ssh/ansiblekey.pub ansible@10.0.2.4
- ssh-copy-id -i ~/.ssh/ansiblekey.pub ansible@10.0.2.5

## Information - ansible_web_and_db
```
.
├── ansible_web_and_db
│   ├── ansible.cfg
│   ├── dbserver.yml
│   ├── production
│   ├── roles
│   │   ├── dbserver
│   │   │   ├── defaults
│   │   │   │   └── main.yml
│   │   │   ├── handlers
│   │   │   │   └── main.yml
│   │   │   ├── meta
│   │   │   │   └── main.yml
│   │   │   ├── README.md
│   │   │   ├── tasks
│   │   │   │   └── main.yml
│   │   │   ├── tests
│   │   │   │   ├── inventory
│   │   │   │   └── test.yml
│   │   │   └── vars
│   │   │       └── main.yml
│   │   └── webserver
│   │       ├── defaults
│   │       │   └── main.yml
│   │       ├── handlers
│   │       │   └── main.yml
│   │       ├── meta
│   │       │   └── main.yml
│   │       ├── README.md
│   │       ├── tasks
│   │       │   └── main.yml
│   │       ├── templates
│   │       │   ├── httpd.j2
│   │       │   └── index.j2
│   │       ├── tests
│   │       │   ├── inventory
│   │       │   └── test.yml
│   │       └── vars
│   │           └── main.yml
│   ├── staging
│   └── webserver.yml
└── README.md
```
1. ansible.cfg    - configuration file what we will use
2. dbserver.yml   - playbook to run dbserver role on dbservers host group
3. webserver.yml  - playbook to run webserver role on webservers host group
4. production     - hosts inventory file
5. roles/         - directory for roles run in our playbooks

