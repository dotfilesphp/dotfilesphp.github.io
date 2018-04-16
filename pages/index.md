## Features
Our goal is to help you make **one dotfiles backup** for every machine.
Here's some feature available in dotfiles manager: 

-  Easy setup and configuration.
-  Backup and restore based on spesific machine.
-  With ``patch`` you can customize your dotfiles for every machine.
-  With ``hooks`` you can define command like adding ssh keys or
   gpg account into your favorite shell script, and have them executed
   during restore process.
   so you can your ssh key  or gpg key into your account
-  If you want you can even test your dotfiles backup in docker
   and have phpunit or behat to do tests.
-  Plugins can help you install/restore command line application like
   ``composer`` or ``nvm``.


## Installation
``` language-bash
wget -c https://dotfilesphp.github.io/latest.phar > dotfiles
chmod +x dotfiles
# Move dotfiles to somewhere can be found by your $PATH
mv dotfiles /home/your-username/bin
```
Initiallize your dotfiles installation:

``` language-bash
dotfiles init
Please enter local backup dir: $HOME/dotfiles-backup
Please enter your machine name: $HOSTNAME
Please enter your install dir: $HOME/.dotfiles
```

## Using dotfiles

### Dotfiles Shell

Executing dotfiles without using any argument will bring you into dotfiles shell:



``` language-bash
cd $HOME/dotfiles-backup
dotfiles
```
The command will creating output like:

``` language-bash
Welcome to the dotfiles.

At the prompt, type help for some help,
or list to get a list of available commands.

To exit the shell, type ^D.

dotfiles>>
```

To exit shell just press ``Ctrl+d`` key.

### Start Backup

Start backup your dotfiles by using dotfiles shell:

``` language-bash

# display how to use add command
dotfiles>> help add

# add .bash rc file
dotfiles>> add .bashrc 

# add .ssh directory but only for this machine
# (you must use -r option to add directory)
dotfiles>> add .ssh -m -r
```

Commit your dotfiles backup into git repo:

``` language-bash
cd /path/to/backup
git init
git add . -A
git commit -am "initial backup"
```

## Restore your dotfiles

Use dotfiles ``restore`` command to restore your dotfiles backup:

```language-bash
dotfiles restore
```
