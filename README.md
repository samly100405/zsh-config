# the best zsh config for beginners

[![Full Video](https://img.youtube.com/vi/8PRP1Z5s2WY/0.jpg)](https://youtu.be/8PRP1Z5s2WY)


## 1:53 - installing zsh

For Ubuntu:
```sh
sudo apt install zsh
chsh -s $(which zsh)
```

Now, log out of your system and log back in.

Use

```sh
echo $SHELL
```

to confirm that zsh is your default shell.

## 2:08 - how to use .zshrc

Check if you already have a .zshrc file:

```sh
ls -f | grep ".zshrc"
```

If you do, use 

```sh
mv .zshrc .zshrc.bak
```

to create a back up of your existing .zshrc file.

Then use

```sh
touch .zshrc
```

to create a new .zshrc file.

## 2:52 - installing and enabling zsh plugins

Use 

```sh
mkdir ~/zsh_plugins
cd ~/zsh_plugins
```

to create a new directory to store your plugins.

```sh
git clone --depth=1 git@github.com:marlonrichert/zsh-autocomplete.git
git clone --depth=1 git@github.com:zsh-users/zsh-syntax-highlighting.git
```

## 3:40 - enabling zsh plugins 

Add these lines to your `.zshrc` file to enable zsh-autocomplete and zsh-syntax-highlighting.

```sh
setopt interactivecomments
source ~/zsh_plugins/zsh-autocomplete/zsh-autocomplete.plugin.zsh

source ~/zsh_plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

Do not enable p10k yet as that requires additional terminal configuration.

## 4:06 - enabling p10k

First, install a nerd font from www.nerdfonts.com and enable it as your terminal font. I personally use JetBrains Mono.

Add this line to your `.zshrc` file to enable p10k.

```sh
source ~/zsh_plugins/powerlevel10k/powerlevel10k.zsh-theme
```

Open a new terminal session and complete the p10k configuration wizard.

Enable instant prompt and save changes to `zshrc`.

### 5:11 - organizing your .zshrc

Move the lines around so that your `.zshrc` file looks like this.

```sh
# Enable Powerlevel10k instant prompt. Should stay close to the top of ~/.zshrc.
# Initialization code that may require console input (password prompts, [y/n]
# confirmations, etc.) must go above this block; everything else may go below.
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

source ~/zsh_plugins/powerlevel10k/powerlevel10k.zsh-theme
# To customize prompt, run `p10k configure` or edit ~/.p10k.zsh.
[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh

setopt interactivecomments
source ~/zsh_plugins/zsh-autocomplete/zsh-autocomplete.plugin.zsh

source ~/zsh_plugins/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```

This way, the commands responsible for each plugin are grouped together.

## 5:37 - final configurations

Add this line to give your autocomplete menu some color.

```sh
zstyle ':completion:*' list-colors "${(s.:.)LS_COLORS}"
```

Add these lines to improve the history search feature.
```sh
HISTSIZE=5000
HISTFILE=~/.zsh_history
SAVEHIST=$HISTSIZE
HISTDUP=erase
setopt hist_ignore_all_dups
setopt hist_save_no_dups
setopt hist_ignore_dups
setopt hist_find_no_dups
setopt hist_ignore_space
bindkey '^p' history-search-backward
bindkey '^n' history-serach-forward
```

### 6:20 - how to use aliases

Add this line to make your `ls` command always be colorful.

```sh
alias ls="ls --color"
```

Add these lines to shorten some common git commmands.

```sh
alias ga="git add"
alias gc="git commit -m"
alias gst="git status"
```