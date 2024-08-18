# the best zsh config for beginners

[![Full Video](https://img.youtube.com/vi/8PRP1Z5s2WY/default.jpg)](https://youtu.be/8PRP1Z5s2WY)


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

Then use


```sh
git clone --depth=1 git@github.com:marlonrichert/zsh-autocomplete.git
git clone --depth=1 git@github.com:zsh-users/zsh-syntax-highlighting.git
git clone --depth=1 git@github.com:romkatv/powerlevel10k.git
```

to download all the plugins.