** Ansible **

Install ansible on ubuntu 20.04
1. sudo apt-get update
2. sudo apt-get install ansible

Master, slave configuration using ssh keys
1. Generate ssh key on master
2. Copy public key into slave authorized_keys file in $HOME/.ssh/ directory
3. Test the connection by logging into salve from the master using ssh command
    ssh <IP>        -- ssh 1.2.3.4
    ssh user@<IP>   -- ssh ubuntu@1.2.3.4


Add entry in ansbile host to call ansible
1. Go to path where hosts file keeps - ex /etc/ansible/hosts
2. Add entry in host file for slave
    [web]
    slave1 ansible_ssh_host=1.2.3.4
3. Test the connection using the ansible ping module
    ansible -m ping all/web/slave1

    a. all - it will call all the hosts that has entry in hosts file
    b. web - its a group, when call web, all the ip's under this group will be called
    c. slave1 - it will call only slave1 host

