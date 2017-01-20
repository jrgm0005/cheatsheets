# Laravel 5.3

0. database settings

    It is recommendable to configure DB in these files in order to everything with DB works fine.
    ````
    app/config/database.php
    .envf
    ````
    
0. Launch server

    ````
    php artisan serve --host 0.0.0.0
    ````    

0. Refresh and seed DB

    ````
    php artisan migrate:refresh --seed
    ````

0. Run mysql in vagrant machine.
    ````
    mysql -uroot -ppassword
    ````


0. Imports model/collections to CSV

    http://csv.thephpleague.com/
    
    http://csv.thephpleague.com/installation/
    
    http://csv.thephpleague.com/examples/
    
0. Start job queue
    ````
    php artisan queue:listen database --tries=2 --timeout=900
    ````
    
    For docker server use 1800 timeout, it is slower than production.
    ````
    php artisan queue:listen database --tries=2 --timeout=1800
    ````
    
0. Log in laravel are in storage/logs. For daily logs change in config/app.config log config to 'daily'.

0. Launch a new migration for add/remove some columns.

    http://stackoverflow.com/questions/16791613/add-new-column-migrate-to-database
