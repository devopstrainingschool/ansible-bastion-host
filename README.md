# ansible-bastion-host
```
bastion ansible_user=centos ansible_host=3.14.244.129

[nodes]
172.31.5.117
172.31.10.162
172.31.12.130

[nodes:vars]
ansible_port = 22   # remote servers port ( not bastion)
ansible_ssh_user = centos  # remote servers users (not bastion)
private_key_file = ~/.ssh/id_rsa       # key to connect to the bastion( in ansible server)
ansible_ssh_common_args= -o StrictHostKeyChecking=no -o ProxyCommand="ssh -q centos@3.14.244.129 -i ~/.ssh/id_rsa -W %h:%p"
```
#### ansible_ssh_common_args= -o StrictHostKeyChecking=no -o ProxyCommand="ssh -q bastionuser@bastionip -i ~/.ssh/id_rsa(inside the batsion) -W %h:%p"
## This one works too
```

[nodes]
172.31.5.117
172.31.10.162
172.31.12.130

[nodes:vars]
ansible_port = 22
ansible_ssh_user = centos
private_key_file = ~/.ssh/id_rsa
ansible_ssh_common_args= -o StrictHostKeyChecking=no -o ProxyCommand="ssh -q centos@3.14.244.129 -W %h:%p"
```
### This one works too but in one conditions, copy ssh key from ansible server to bastion , then create another ssh key in bastion then copy it other servers
```

[nodes]
172.31.5.117
172.31.7.75
172.31.10.162
172.31.12.130

[nodes:vars]
ansible_port = 22
ansible_ssh_user = centos
ansible_ssh_common_args= -o StrictHostKeyChecking=no -o ProxyCommand="ssh -q centos@3.14.244.129 -W %h:%p"
```
![image](https://github.com/devopstrainingschool/ansible-bastion-host/assets/107158398/f957c078-9b83-4020-aaf7-6530558b39a5)

