# Quick Start Guide - JR CHEATSHEET


## Chrome plugins

0. AdBlock
0. Postman (Launch http calls)
0. DHC Plugin (Launch http calls)


## Console plugins for gitbash

Crear archivo .bashrc en el raiz del usuario c:/Users/User
Create .bashrc file in user's folder (c:/Users/Username)

How to create a .bashrc file in order to add aliases.

.bashrc is located at user folder (could be hidden)

### Script for auto-add ssh keys

Add in .bashrc

    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_rsa

ALIASES
---


Añadir al fichero la siguiente configuracion
Add to .bashrc file next script

````   
#-------------------
# Personal functions
#-------------------
#Function to get the current git branch (on windows OS)
function current_branch() {
    ref=$(git symbolic-ref HEAD 2> /dev/null) || return
    echo ${ref#refs/heads/}
}    

function gpull() {
    git pull origin $(current_branch)
}

function gpush() {
    git push origin $(current_branch)
}

#-------------------
# Personal Aliases
#-------------------

alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'
# -> Prevents accidentally clobbering files.
alias mkdir='mkdir -p'

alias h='history'
alias j='jobs -l'
alias which='type -a'
alias ..='cd ..'

# Pretty-print of some PATH variables:
alias path='echo -e ${PATH//:/\\n}'
alias libpath='echo -e ${LD_LIBRARY_PATH//:/\\n}'


alias du='du -kh'    # Makes a more readable output.
alias df='df -kTh'

#-------------------------------------------------------------
# The 'ls' family (this assumes you use a recent GNU ls).
#-------------------------------------------------------------
# Add colors for filetype and  human-readable sizes by default on 'ls':
alias ls='ls -h --color'
alias lx='ls -lXB'         #  Sort by extension.
alias lk='ls -lSr'         #  Sort by size, biggest last.
alias lt='ls -ltr'         #  Sort by date, most recent last.
alias lc='ls -ltcr'        #  Sort by/show change time,most recent last.
alias lu='ls -ltur'        #  Sort by/show access time,most recent last.

# The ubiquitous 'll': directories first, with alphanumeric sorting:
alias ll="ls -lv --group-directories-first"
alias lm='ll |more'        #  Pipe through 'more'
alias lr='ll -R'           #  Recursive ls.
alias l='ll -A'           #  Show hidden files.
alias tree='tree -Csuh'    #  Nice alternative to 'recursive ls' ...

#
# Aliases for git
# (sorted alphabetically)
#

alias g='git'
alias ga='git add'
alias gaa='git add --all'
alias gapa='git add --patch'
alias gp='git pull'
alias gpodev='git pull origin develop'
alias gst='git status'

alias gb='git branch'
alias gba='git branch -a'
alias gbda='git branch --no-color --merged | command grep -vE "^(\*|\s*(master|develop|dev)\s*$)" | command xargs -n 1 git branch -d'
alias gbl='git blame -b -w'
alias gbnm='git branch --no-merged'
alias gbr='git branch --remote'
alias gbs='git bisect'
alias gbsb='git bisect bad'
alias gbsg='git bisect good'
alias gbsr='git bisect reset'
alias gbss='git bisect start'

alias gc='git commit -v'
alias gc!='git commit -v --amend'
alias gcn!='git commit -v --no-edit --amend'
alias gca='git commit -v -a'
alias gca!='git commit -v -a --amend'
alias gcan!='git commit -v -a --no-edit --amend'
alias gcans!='git commit -v -a -s --no-edit --amend'
alias gcam='git commit -a -m'
alias gcb='git checkout -b'
alias gcf='git config --list'
alias gcl='git clone --recursive'
alias gclean='git clean -fd'
alias gpristine='git reset --hard && git clean -dfx'
alias gcm='git checkout master'
alias gcd='git checkout develop'
alias gcmsg='git commit -m'
alias gco='git checkout'
__git_complete gco _git_checkout
alias gcount='git shortlog -sn'
compdef gcount=git
alias gcp='git cherry-pick'
alias gcpa='git cherry-pick --abort'
alias gcpc='git cherry-pick --continue'
alias gcs='git commit -S'
alias gd='git diff'
alias gdca='git diff --cached'
alias gdct='git describe --tags `git rev-list --tags --max-count=1`'
alias gdt='git diff-tree --no-commit-id --name-only -r'
alias gdw='git diff --word-diff'
alias gf='git fetch'
alias gfa='git fetch --all --prune'
alias gfo='git fetch origin'
branch=$(git symbolic-ref HEAD | sed -e 's,.*/\(.*\),\1,')
#alias gpush='git push origin $(git branch | sed -n -e "s/^\* \(.*\)/\1/p")'
#alias ggpush='git push origin $(git branch | sed -n -e "s/^\* \(.*\)/\1/p")'
#alias ggpush='git push origin $(git_current_branch)'
#alias ggpusht='git push -u origin $(git_current_branch)'

#Script to auto add ssh-keys
#It will be executed always when git bash is launched

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa

````

0. Run mysql in vagrant machine.
    ````
    mysql -uroot -ppassword
    ````
