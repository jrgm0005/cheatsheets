# Ubuntu common commands

- - - 

1. Start MySQL service

        sudo /sbin/service mysqld start       
        
2. Start SSH-AGENT

        eval "$(ssh-agent -s)"
        
3. Add ssh key to SSH-AGENT (needed for git)

        ssh-add ~/.ssh/id_rsa
       
4. Start Laravel server to debug

        php artisan serve --host 0.0.0.0
