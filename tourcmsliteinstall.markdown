# How To Install Tour CMS Lite on Windows.

##Steps.

0. Run Console and Virtual Box as administrator. If do not run this, syslinks will run wrong.

0. Go to your project folder and download the vagrant machine.
    
        Git clone git@gitlab.com:veleta-solutions/vagrantprovisioning.git
 
0. Edit config.yaml in your vagrant configuration. Have to add your gitlab_user your ssh keys and your workspace path.

0. Review your bootstrap.sh and check that steps 5-6 are currently in your file, in another case, add them to your bootstrap file.

0. Add right access to ssh keys in bootstrap.sh file (just after install selenium in bootstrap.sh)
````
     # change permission to ssh keys
     cd .ssh
     sudo chmod 600 /home/vagrant/.ssh/veleta_rsa.pub
     sudo chmod 600 /home/vagrant/.ssh/veleta_rsa
     cd ..
     # change permission to ssh keys
````

0. Change this lines in bootstrap.sh
````
     mkdir workspace >> mkdir workspace_project
     cd workspace    >> cd workspace_project
````

0. vagrant up (It takes a long time, probably between 15 & 20 minutes)

0. Vagrant ssh

0. Install dependencies. Go to project folder and run this command.

    ````
    bundle install
    ````

0. Launch local database running this command.

    ````
    bundle exec rake db:create && rake db:migrate
    ````
    
0. Run 2 console. In one, run rails server, in another one run grunt server using the next commands.

    Rails, in your project folder
    ````
    rs
    ````
    Grunt, in your project folder/client
    ````
    grunt server
    ````
    
0. In your browser go to the next.

       [ http://localhost:9000/#/submit.html ]( http://localhost:9000/#/submit.html  "Local server")