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

### Please change the instance ip before using the these instructions.

* if you don't have whois installed, then install it by
        sudo apt-get install whois

*  Create a sudo password for the ubuntu user
        
        mkpasswd --method=SHA-512

    > this will ask you for a password enter the password you intend to give to the ubuntu user
    > and keep the output for further use. Lets name it our_ubuntu_passwod.

*  use the following command to run this recipie:
        
        ansible-playbook -i hosts playbook.yml --extra-vars="ssh_port=22" --extra-vars="ubuntu_sudo_password=our_ubuntu_password"

        > make sure your inside secure_do directory
        (e.g) ansible-playbook playbook.yml -i hosts --extra-vars='ssh_port=22' --extra-vars='ubuntu_sudo_password=$6$qzYuUSMNbNW$NZQUHLkYwrLFv//y7K9SQktwejlvlJz2laq1VOCRzrt4fdVzStS5jSTemwcBQqP.O54MHD0974RU.XvkzeYSW.'

    > after this playbook is run use the following commmand to connect to the system.

        ssh ubuntu@instance-ip
        or
        ssh -p ssh_port ubuntu@instance-ip

