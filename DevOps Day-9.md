---
date: 2025-06-26T11:00
tags: []
share_link: https://share.note.sx/ub1wcsam#HZq/mdKWORJjCdV91Vs4YM7XigT4NQQNBzTGkn+o8Js
share_updated: 2025-06-26T13:23:49+08:00
---

# Ansible

first of this thing works on the Linux OS.
This is a Automation tool used to Configuration Management, Application Deployment, Task Automation, Provisioning servers, and Orchestration of complex workflow  
This is a 

This is one of the most used Configuration Management Tools and Automation Tool.

#### Playbook with mean YML file

--> Configuration Management {handling changes in a system so that it maintains integrity over time.}

```embed
title: "Welcome to The Apache Software Foundation"
image: "https://www.apache.org/images/ASF_CommunityOverCode_Banner_Asia.jpg"
description: "Home page of The Apache Software Foundation"
url: "https://www.apache.org/"
favicon: ""
aspectRatio: "33.33333333333333"
```


### --> Configuration management and automation tools

-> Ansible 
-> Chef
-> TerraForm

There are other also but these are the most famously used Configuration management and automation tool

## DO to it with the Ansible on AWS -->

Remember to create a key pair (.pem file) when creating an Instance..

Create -> in AWS 
ansible-aws-project/
├── inventory.ini
├── playbook.yml
└── files/
    └── index.html


in `inventory.ini`

```ini
[web] 
13.233.251.15 ansible_user=ec2-user ansible_ssh_private_key_file=./ansible-key.pem
```
-remove the `<` and `>` and replace the IP from the IP given on Instance

in `playbook.yml`

```yml
---
- name: Setup Apache Web Server on AWS EC2
  hosts: web
  become: true

  tasks:
    - name: Install Apache (Amazon Linux)
      yum:
        name: httpd
        state: present

    - name: Copy HTML file
      copy:
        src: file/index.html
        dest: /var/www/html/index.html

    - name: Start Apache service
      service:
        name: httpd
        state: started
        enabled: true
```

and in `index.html`

```html
<!DOCTYPE html> 
 <html> 
 <head> 
 <title>Welcome to Ansible Web Server</title> 
 </head> 
 <body> 
 <h1>Hello worldo from your Apache server on AWS EC2!</h1> 
 <p>Deployed using Ansible </p> 
 </body> 
 </html>
```

now in your local computer open cmd in the folder where your .pem file is located and run
`ssh -i your-key-pair.pem ec2-user@13.233.251.15`
replace your key pair and IP given with the given Instance key pair(.pem) and IP

After doing this 
`cd ansible-aws-project`
and run
```bash
chmod 400 ansible-key.pem #giving permission
    
ansible-playbook -i inventory.ini playbook.yml #this will lauch the cloud ansible web

```


Now in your AWS go to `EC2 > Network & Security > Security Groups` 
Under that find the `lauch-wizard-?` of your instance
After that `-> Edit Inbound rules`
Delete the default rule and 
create two new rule 
    └── First Rule -> `Type > HTTP`, `CIDR Block > 0.0.0.0/0`
    └──Second Rule -> `Type > HTTP`, `CIDR Block > ::/0`

Then `Save Rule`

and then on the new tab search for http://13.233.251.15/ (replace the IP with the Instance IP)