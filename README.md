# secure_do
Ansible recipe to secure ubuntu installation on digital ocean

## Enviorment:

This recipie works perfectly fine with the following: 

*  ansible 1.7.2
*  distribution

        Distributor ID:  Debian
        Description:    Debian GNU/Linux testing (stretch)
        Release:    testing
        Codename:   stretch
*  digitalocean instance setup with a ssh-key

## Steps to use

*  Create a sudo password for the ubuntu user
        
        mkpasswd --method=SHA-512

    > this will ask you for a password enter the password you intend to give to the ubuntu user
    > and keep the output for further use. Lets name it our_ubuntu_passwod.

*  use the following command to run this recipie:
        
        ansible-playbook -i hosts playbook.yml --extra-vars="ssh_port=22" --extra_vars="ubuntu_sudo_password=our_ubuntu_password"

    > after this playbook is run use the following commmand to connect to the system.

        ssh ubuntu@instance-ip
        or
        ssh -p ssh_port ubuntu@instance-ip

