# macos-sysconfigs

a collection of system configs and other scripts that are hand to have

## bash_profile
```# Exports
export PATH="/usr/local/bin:/usr/local/sbin:/Users/john/Repos/aws-profile-bash-prompt:$PATH"
export EDITOR='vim'

# Set default editor
EDITOR=vim

# Configure command line colors
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad


# Set color variables
BLACK="\[\e[0;30m\]"
DARK_GRAY="\[\e[1;30m\]"
RED="\[\e[0;31m\]"
YELLOW="\[\e[0;33m\]"
PURPLE="\[\e[1;34m\]"
BLUE="\[\e[0;34m\]"
LIGHT_BLUE="\[\e[1;34m\]"
GREEN="\[\e[0;32m\]"
LIGHT_GREEN="\[\e[1;32m\]"
CYAN="\[\e[0;36m\]"
LIGHT_CYAN="\[\e[1;36m\]"
LIGHT_RED="\[\e[1;31m\]"
PURPLE="\[\e[0;34m\]"
LIGHT_PURPLE="\[\e[1;35m\]"
BROWN="\[\e[0;33m\]"
LIGHT_GRAY="\[\e[0;37m\]"
WHITE="\[\e[1;37m\]"


# Change command prompt display
function parse_git_branch {
   git branch --no-color 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
export PS1="\[${LIGHT_GRAY}\][\[${LIGHT_GREEN}\]\u\[${LIGHT_GRAY}\]]\[${LIGHT_GRAY}\]:|\[${LIGHT_GREEN}\]\h\[${LIGHT_GRAY}\]:|\[${LIGHT_CYAN}\]\w\[${LIGHT_GRAY}\]:\[${LIGHT_PURPLE}\]\$(parse_git_branch)\[${LIGHT_GRAY}\]:| \[${WHITE}\]"

# Go up one directory every . in the argument.
# For example, to go up 4 directories (cd ../../../..)
# type: .. ....
..() {
  local times
  times=$(echo $1 | wc -c)
  for ((i = 1; i < $times ; i++)); do
    cd ..
  done
}

# Get a human readable date string
hdate() {
  date "+%Y-%m-%d_%H-%M-%S"
}

#Aliases
alias ll='ls -alGFh'
alias repos='cd ~/Repos'

#Functions - System

cd () {
    builtin cd "$@"
    ll
}

#System Color goodies
export CLICOLOR=1
export LSCOLORS="ExFxCxDxBxegedabagacad" # Example colors, customize as needed

#Git Goodies
gc () {
    git clone "$@"
}

ginit() {
    git init
}

gcom() {
    git add .
    git commit -am "$@"
    git push

}

gdiff() {
    git diff

}

gnewb() {
    git branch "$@"

}

gchbranch() {
    git checkout "$@"

}

gmerge () {
    git merge "$@"
}

grebase () {
    git rebase "$@"
}
