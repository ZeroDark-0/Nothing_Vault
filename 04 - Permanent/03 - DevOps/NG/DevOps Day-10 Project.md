---
date: 2025-06-27T21:27
tags: []
---

### <code style="color:cyan">Using Ansible to provision an EC2 instance and automate the installation of Docker. Then, deploy an Nginx container that serves a custom HTML landing page.</code>

- AWS CLI configured (`aws configure`)
    
- Ansible installed (`ansible --version`)
    
- A `.pem` key file downloaded from AWS (e.g., `pass3.pem`)
    
- and also Installing the `python` , `boto3`, `botocore`

ec2_nginx_simple/
├── create_ec2.yml         # Playbook to launch EC2 instance
├── setup_nginx.yml        # Playbook to install Docker & run Nginx
├── index.html             # Custom landing page
├── inventory.ini          # Ansible inventory file
├── pass3.pem              # Your EC2 private key


--> Step-1
    uploading the .pem file to the AWS console
 
 `ssh -i <pem-file-name>.pem ec2-user@<public-ip>`
 after get connected `exit` that
 `scp -i <pem-file>.pem <pem-file>.pem ec2-user@<public-ip>:<path>`

--> then on AWS console 
`chmod 400 ~/ec2_nginx_simple/pass3.pem`

Step-2 -> creating files

`create_ec2.yml`
```yml
- name: Provision EC2 instance
  hosts: localhost
  gather_facts: no
  vars:
    key_name: <pem-file-name>
    instance_type: t2.micro
    region: <region>                  
    ami: ami-0a7cf821b91bcccbc
  tasks:
    - name: Launch EC2
      amazon.aws.ec2_instance:
        name: nginx-server
        key_name: "{{ key_name }}"
        instance_type: "{{ instance_type }}"
        region: "{{ region }}"
        image_id: "{{ ami }}"
        wait: yes
        count: 1
        network:
          assign_public_ip: true
        tags:
          Name: nginx-server
      register: ec2

    - name: Add EC2 to inventory
      add_host:
        name: "{{ item.public_ip }}"
        groups: launched
      loop: "{{ ec2.instances }}"

    - name: Wait for SSH
      wait_for:
        host: "{{ item.public_ip }}"
        port: 22
        delay: 10
        timeout: 300
        state: started
      loop: "{{ ec2.instances }}"
```

`inventory.ini`

```ini
[launched]
<public-ip>  ansible_user=ec2-user ansible_ssh_private_key_file=./<pem-file>.pem

```

`index.html`

```html
<h1>Hello from Ansible + Docker + Nginx!</h1>
```

`setup_nginx.yml`

```yaml
- name: Setup Docker and run Nginx
  hosts: launched
  become: true
  vars:
    ansible_ssh_private_key_file: ./<pem-file-name>.pem
  tasks:
    - name: Install Docker
      amazon.aws.package:
        name: docker
        state: present

    - name: Start Docker
      ansible.builtin.service:
        name: docker
        state: started
        enabled: true

    - name: Create web folder
      file:
        path: /home/ec2-user/web
        state: directory
        owner: ec2-user
        group: ec2-user
        mode: '0755'

    - name: Upload custom index.html
      copy:
        src: ./index.html
        dest: /home/ec2-user/web/index.html
        owner: ec2-user
        group: ec2-user
        mode: '0644'

    - name: Run Nginx container
      community.docker.docker_container:
        name: nginx
        image: nginx
        state: started
        restart_policy: always
        ports:
          - "80:80"
        volumes:
          - "/home/ec2-user/web:/usr/share/nginx/html"
```


Step-3 ->Run on AWS console

`ansible-playbook create_ec2.yml`

```bash
aws ec2 describe-instances \
  --filters "Name=tag:Name,Values=nginx-server" \
  --query "Reservations[*].Instances[*].PublicIpAddress" \
  --output text \
  --region ap-south-1
```

Step-4 ->Allow Port 80

```bash 
aws ec2 describe-instances \
  --filters "Name=tag:Name,Values=nginx-server" \
  --query "Reservations[0].Instances[0].SecurityGroups[0].GroupId" \
  --region ap-south-1 \
  --output text

```

```bash
aws ec2 authorize-security-group-ingress \
  --group-id <sg-id> \
  --protocol tcp \
  --port 80 \
  --cidr 0.0.0.0/0 \
  --region ap-south-1
```

Step-5 ->deploy ngixn

`ansible-playbook -i inventory.ini setup_nginx.yml`


Finally search `http://<your-ec2-ip>` on a new tab

