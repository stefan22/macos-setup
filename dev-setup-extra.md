# Dev-Setup

<br />

1._ Add Git Global config      
2._ Add SSH to Github      
3._ Update to the latest version of NPM && config      
4._ Add Aliases and Git Completions       
<br />
Run script and re-start the terminal. Then
<br />

#### Add Git Global Config
```js
git config --global user.name "Your Name"
git config --global user.email "you@your-domain.com"

git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```


#### Add SSH to Github
```js
// 1. Create SSH dir.
mkdir ~/.ssh

// 2. Run on terminal:
ssh-keygen -t ed25519 -C "github"

/* enter:
	github as file name
    secret passphrase
*/

//ssh dir permissions --> drwx--x--x
     
// 3. In SSH dir, create a config file, and add:

Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/github

// 4. Add key to Apple keychain
ssh-add --apple-use-keychain ~/.ssh/github

// 5. Copy/paste key to Git account settings
cat ~/.ssh/github.pub | pbcopy
```

#### NPM
```js
//Update to latest LTS version (nvm already installed)
nvm install --lts
npm install -g npm@latest
//User config
npm set init-author-name="your name"
npm set init-author-email="you@example.com"
```


#### Git Completions
```js
//Install git completions at /.oh-my-zsh/custom/plugins
git clone https://github.com/zsh-users/zsh-completions.git

//Add aliases file to /.oh-my-zsh/custom

//Update .zshrc cp & paste on terminal
fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src
autoload -U compinit && compinit
source "$ZSH/oh-my-zsh.sh"
```

<br />

#### ZSH file
```shell

# -------------------------------------------------------------------------------
#   ZSH Configuration 
# -------------------------------------------------------------------------------
#
# -- 1. Basic shell settings -------------------------------------------------------
##
#
PS1='%n@%m %~$ '
setopt NO_BEEP           # disable terminal bell
setopt HIST_IGNORE_SPACE # ignore commands that start with a space


# -- 2. Environment variables ------------------------------------------------------
##
#
export ZSH="$HOME/.oh-my-zsh/"            # path to Oh My Zsh
export LANG=en_US.UTF-8                   # local language env
export MANPATH="/usr/local/man:$MANPATH"
export ARCHFLAGS="-arch $(uname -m)"     # compilation flags

export PATH="/opt/homebrew/bin:$PATH"


# -- 3. Oh MyZsh -------------------------------------------------------------------
## 
#
zstyle ':omz:update' mode reminder                                                # remind me when new updates
fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src     # Completions plugin path
autoload -U compinit && compinit
#
plugins=(
  zsh-completions
)
#

autoload -U compinit && compinit
source $ZSH/oh-my-zsh.sh
# 
eval "$(starship init zsh)".   # loading starship theme
#
#
# ----------------------------------------------------------------------------------
# -- 4. Homebrew packages ----------------------------------------------------------
# ----------------------------------------------------------------------------------
##
#
#Add the following to your shell profile e.g. ~/.profile or ~/.zshrc:
export NVM_DIR="$HOME/.nvm"
  [ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"  # This loads nvm
  [ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion

###
##
#
#
# -- The End ------------------------------------------------------------------------------------------------------------------------------------------
eval "$(starship init zsh)"

# removed lm studio
```



:100:
