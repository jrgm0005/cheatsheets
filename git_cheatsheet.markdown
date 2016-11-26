# GIT Cheatsheet

## GIT
---

###SSH KEYS ERRORS
---
Para añadir las claves, hacerlo en windows en la carpeta raíz del usuario
USER/.ssh añadir la clave y fijarse en los permisos.

Si da errores, fijarse en que esté el ssh-agent activo para que la detecte y en el fichero config con la ruta válida.

---
###How to do a commit

1. Add new files
2. Commit with a ***DESCRIPTIVE*** message

###How to do a push request

1. Update files in develop branch (PULL)
2. Change to working branch
3. PUSH

### How to clean commits and rebase

   0. Before upload.
        
        1. git add .
        2. git commit -m "..."
        3. git status 

   0. Git rebase -i < hash of last commit before commits to rebase >

        Will show all commits.
        We choise the first one and note the rest with 's' to squash.
        This option will merge all commits in the first one.
        Save.
        Quit.
        Rename the commit message(which we will see as commit message).
        # for comment the others commit messages.
    
   0. Go to develop
    
        git checkout develop
            
   0. git pull 
   0. return to our branch

        git checkout branch
                  
   0. git rebase develop

        Conflicts or not
    
   0. git mergetool -t diffmerge
   0. git rebase -- continue
   0. Clean files from merge...
   ````
   git clean -f
   ````
   
   0. git push origin branch -f

        Forced because we changed the log of GIT

### Git Actions CheatSheet (most used commands)

0. Go to a branch

        git checkout branchname
        alias: gco

0. Do a pull (Update data)

        git pull
        alias: gp

0. Create and move to a new branch

        git checkout -b new_branch_name
        alias: gcb
        
0. Do a pull (Origin)

        git pull origin develop
        alias: gpod
        
0. Upload the current branch

    ````
    git push origin branch
    alias: gpush        
    ````
    
0. Add files to a commit (New and modified files)

    ````
    git add .
    ````

0. Commit with new files

    ````
    git commit -m "Commit message"
    alias: gcmsg
    ````

0. Upload branch with files merged

    ````
    git rebase #branch
    git rebase develop
    alias: grd
    ````
    
0. Download remote branch
    
    ````
    git branch --track <nombre_branch_local> origin/<nombre_branch_remote> 
    ````