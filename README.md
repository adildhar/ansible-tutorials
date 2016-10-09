# Ansible Quick Tutorials with examples
### These notes are for Ansible Quick Tutorials with examples

The notes provide examples for logic and do  not most implement anything. These examples have been tried vagrant.


1) Vagrant setup with Ansible (ansible-local) provisioner

Vagrant File
````
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "private_network", type: "dhcp"
  config.ssh.insert_key = false
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.verbose        = true
    ansible.install        = true
    ansible.limit          = "all" # or only "nodes" group, etc.
  end
end
``````

2). Basic Ansible commands 

Running adhoc command without playbook
```````````````
ansible all -i "localhost," -c local -m shell -a 'echo hello world'
``````````````
Running with the playbook
`````````````````````
ansible-playbook -i "localhost," -c local playbook.yml
```````````````````````
Using default inventory file /etc/ansible/hosts. 
Just add an entry for localhost as given below:
``````````
localhost ansible_connection=local
````````````
Now run playbooks in localhost just by saying 

```````````
ansible-playbook playbook.yml
``````````````````

and for adhoc command, 

`````````````````
ansible all -m shell -a 'echo hello world’
```````````````````

3). The Tutorial Wiki link is below

https://github.com/adildhar/ansible-tutorials/wiki
