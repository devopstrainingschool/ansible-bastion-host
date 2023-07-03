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
