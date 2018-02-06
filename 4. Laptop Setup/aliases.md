List of useful aliases you can add to your `~/.bash_profile` file:

```
# Git aliases
alias gs='git status '
alias ga='git add '
alias gb='git branch '
alias gcm='git commit -m'
alias gca='git commit -a'
alias gd='git diff'
alias gco='git checkout '
alias gk='gitk --all&'
alias gx='gitx --all'
alias gpod='git push origin develop'
alias gpom='git push origin master'
alias gpr='git pull --rebase'

# Kubectl aliases
alias kubectl-prod='kubectl config use-context gke_andela-kube_us-east1-b_andela-prod'
alias kubectl-stag='kubectl config use-context gke_microservices-kube_us-east1-c_staging'
```
