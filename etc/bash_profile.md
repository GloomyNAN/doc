# bash_profile


```bash
source ~/.profile

function git_branch {
  branch="`git branch 2>/dev/null | grep "^\*" | sed -e "s/^\*\ //"`"
  if [ "${branch}" != "" ];then
      if [ "${branch}" = "(no branch)" ];then
          branch="(`git rev-parse --short HEAD`...)"
      fi
      echo " ($branch)"
  fi
}
export PS1='\u@\h \[\033[01;36m\]\W\[\033[01;32m\]$(git_branch)\[\033[00m\] \$ '

# Homestead
function homestead() {
    ( cd ~/WorkArea/VMS/Homestead && vagrant $* )
}

function killhomestead() {
     ps -ef|grep VirtualBox|awk '{print  $2}'|xargs kill
}

function delbranch(){
        ( git push origin --delete $1 && git branch -d  $1)
}

# Show Or Hide Hidden Files
function show() {
	defaults write com.apple.finder AppleShowAllFiles TRUE
	killall Finder
}

function hide() {
	 defaults write com.apple.finder AppleShowAllFiles FALSE
    	 killall Finder
}

#React-Native
function rn() {
    ( react-native $* )
}

#if [ -f ~/.bashrc ]; then
#   source ~/.bashrc
#fi

# Add environment variable for laravel installer
export PATH=$PATH:~/.composer/vendor/bin/

alias ..="cd .."
alias ...="cd ../.."
alias h='cd ~'
alias c='clear'
alias icloud='cd ~/Library/Mobile\ Documents/com~apple~CloudDocs'
# Work Places
alias WWW='cd ~/WorkArea/WWW'

# Git
alias pull='git pull origin'
alias merge='git merge'
alias fetch='git fetch'
alias rebase='git rebase'
alias push='git push origin'
alias add='git add -A'
alias commit='git commit -m'
alias checkout='git checkout'
alias status='git status'
alias ll='ls -la'
```

