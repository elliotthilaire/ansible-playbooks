README
======

Ansible playbooks for managing my "stuff".

## Quick start

1. Copy vars/secrets.yml.example and modify it.
2. Modify config/my_ssh_keys_task.yml
3. Create hosts file(s) in hosts/  (I create seperate files for production and testing)

To provision a new server on Digital Ocean run

    ansible-playbook -i hosts/testing playbooks/create_new_droplet.yml

Honestly, using tugboat cli is easier. (This is there for example)


Run this for brand new servers to setup a sudo account and disable root login.

    ansible-playbook -i hosts/testing playbooks/setup_sudo_user.yml

From then on, run something like

    ansible-playbook -i hosts/testing webservers.yml --ask-sudo-pass

Login in run a one off command

    ansible webservers -i hosts/testing -m ping 
    
## Resources

 - http://docs.ansible.com/playbooks_best_practices.html#directory-layout
 - http://practicalops.com/tag/ansible.html
 - https://gist.github.com/phred/2897937
 - https://github.com/cturner80/digital-ocean-ansible/blob/master/tasks/system_updates.yml
 - https://github.com/garethr/ansible-provisioner
 - https://github.com/lorin/ansible-quickref 
 - https://github.com/phred/5minbootstrap/blob/master/bootstrap.yml
 - https://github.com/pvillega/ansible-ec2-play/blob/master/bootstrap.yaml
