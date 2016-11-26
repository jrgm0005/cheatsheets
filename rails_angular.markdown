# RAILS APP + ANGULAR + GIT

    Using Rails 5(Backend), with API option to link with Angular (Front).
    I should create using token auth to link both projects.
    Bundle for Rails dependencies.
    Yeoman for Angular dependencies.

## RAILS

### Create a new project

0. Create a new Rails project. (using mysql as database)

    ````
    rails new project-name --database = mysql
    ````
       
0. If it is needed, create a new mysql user, and grant all permission.

    https://www.digitalocean.com/community/tutorials/crear-un-nuevo-usuario-y-otorgarle-permisos-en-mysql-es
    
### Create Models

0. Create Models
    
    Example
    
    ````
    rails generate model Post title:string article:text author:integer category:integer    
    ````
    
0. Migrate

    ````
    rake db:migrate RAILS_ENV=development
    ````
     
### Create controllers

0. Create Controllers

    ````
    rails generate controller controllername
    ````

### Related links

1. http://iridakos.com/2013/12/07/creating-a-simple-todo-part-1.html
2. http://angular-rails.com/
3. http://www.genbetadev.com/ruby/herramientas-imprescindibles-para-un-desarrollador-de-ruby-on-rails


## ANGULAR


  
0. Install bower JSON

    ````
    https://github.com/rharriso/bower-rails
    ````
    
#GIT

1. Force upload to github

    Create the user, adding ssh-key to ssh-agent using ssh-add.
    Force the push.

        git push -f origin master