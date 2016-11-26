Guide for install vagrant machine
========================

*Guide for Windows*
------------------------

1. Download Virtual Box
	
	https://www.virtualbox.org/

2. Download Vagrant
			
	https://www.vagrantup.com/
	
3. Copy the image (Clone) vagrant box

	https://www.dev-metal.com/copy-duplicate-vagrant-box/
		
4. Add the vagrant box image to vagrant box
	
	    "vagrant box add boxname boxImageURL"

5. Configure public keys in console (And add them to gitlab)

	https://gitlab.com/help/ssh/README
		
6. Add login data to vagrant file (login data and GUI)
    
    Add this new lines inside the Vagrantfile and link it to your host project folder (../gyg in the example)

    ```
    config.vm.network "forwarded_port", guest: 8000, host:8000 #laravel artisan serve
    config.vm.network "forwarded_port", guest: 3306, host:3336 #mysql
    config.vm.network :private_network, ip: "192.168.56.101"
    config.vm.synced_folder "../gyg", "/home/vagrant/workspace/supplier.tourcms.api"
    ```
     Add this code in your vagrant file
    
		# Login data and GUI (For Windows Solutions).
		config.ssh.username = "vagrant"
		config.ssh.password = "vagrant"

		config.vm.provider "virtualbox" do |vb|
		 vb.gui = true
		end

7. Install Ansible using cygwin

	http://everythingshouldbevirtual.com/ansible-using-ansible-on-windows-via-cygwin

8. Install PHP 5.4 on vagrant machine
			
	https://www.mojowill.com/geek/howto-install-php-5-4-5-5-or-5-6-on-centos-6-and-centos-7/
	
        http://sharadchhetri.com/2015/04/04/install-php-5-4-on-centos-6-with-yum-command/

	See comments to install php-mbstring command

	    yum update
	    yum install php-mcrypt*
			
9. Install composer on vagrant machine

	https://getcomposer.org/doc/00-intro.md

10. Create vendor folder on vagrant machine and launch composer install (in tourCMS project folder)
			
11. Launch the server

	       php artisan serve --host 0.0.0.0
	       
	       
Gitlab publick key problem
--------------------------
If you have had problems to download the repo(Gitlab) in your machine and your error msg is seems to this one:

    Permission denied (publickey).
    fatal: The remote end hung up unexpectedly
    
<hr>
NOTE: I was doing this on vagrant machine, so there is a linux     machine(CentOS).       
<hr>  

    
The steps to solve it are the next:

1. Create new ssh-keys and add them to ssh-agent
    
    https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

2. Give permission to your keys

    You should give the next permission (600) it can be done with next command     (It could need sudo permission)
    
        chmod 600 publickey
    
    You should obtain something like that using the command 'ls -al' in the folder

        -rw-------. 1 vagrant vagrant 1675 Sep 15 07:55 sshkey
        -rw-------. 1 vagrant vagrant  416 Sep 15 07:55 sshkey.pub


3. Create the config file in your .ssh folder

    You should create in your .ssh folder a new file called config. You should follow the steps in this URL:
    
    https://gitlab.com/help/ssh/README
    
4. Add public key to your repo(Gitlab)

    https://gitlab.com/profile/keys
    
5. Install composer
6. Launch the server


- - -

## Permit access to mysql from host machine

0. LOCATE my.cnf AND UPDATE BIND
````
sudo updatedb
locate my.cnf
````
Change bind to ->
bind-address = 0.0.0.0

0. Grant permission to root user (outside vagrant machine).
````
GRANT ALL PRIVILEGES ON *.* TO 'root'@'10.0.2.2' WITH GRANT OPTION;
````
'10.0.2.2' is related to mysql workbench in order to connect from host machine.

0. FINALLY RESTART MYSQL SERVICE.
````
sudo service mysql restart
````

## Install PHPUnit for testing

1.    Add this code to composer.json
        
        "require-dev": {
		"phpunit/phpunit": "4.8.*",
		"phpspec/phpspec": "~2.1"
		}
		
2. Download PHPUnit 4.8 and add it to console
    
         wget https://phar.phpunit.de/phpunit-4.8.9.phar
         sudo chmod +x phpunit-4.8.9.phar 
         sudo mv phpunit-4.8.9.phar /usr/local/bin/phpunit
         phpunit --version
         Result >> 'PHPUnit 4.8.9 by Sebastian Bergmann and contributors.'

	