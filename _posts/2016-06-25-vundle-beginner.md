---
title: Vundle for beginner - Vim plugins manager
---

## Vim, plugins and plugin manager
Well, if you're reading this article, then I assume that you already know what Vim editor is. So let me skip the introduce part.

One key feature that makes the power of Vim is the plugin system. Vim let you extends, enhance its power, abilities (and complexities) through the plugins that you can install.

You may have installed some plugins by hand, manually. That's what I did the first time I installed a plugin: download the plugin, untar, put the files in some specified directories, even need to run some additional commands to make it work.

Maybe that method is easy for you. But the problem is we often don't install just 1 or 2 plugin. There are thousand of plugins, and you may love to install dozens of them. Installing all of them manually is a very tedious work. Let imagine you have a dozen plugins that you use them every day. And one day you get a new machine where none of your favourite plugins is there. It could be painful & boring task to have to manually download and install all of them by hand. :dizzy_face:

That's why we should use a plugin manager to automate the process of setting up our plugins, and manage them for us. By "manage", I mean the tasks of tracking, updating, uninstalling, etc. the plugins that were installed.

There are many options for you to choose a plugin manager for Vim. Take a quick search on Google and you will see some names like Vundle, Pathogen, vim-plug, etc.. In this specific post, I will talk about Vundle. Why? Because I haven't used the others :innocent: 

## What is Vundle?
[Vundle] is a Vim plugin that, well, manages other plugins (and even itself). From the [introduction](https://github.com/VundleVim/Vundle.vim/blob/master/README.md):

> Vundle allows you to...
>
> * keep track of and configure your plugins right in the `.vimrc`
> * install configured plugins (a.k.a. scripts/bundle)
> * update configured plugins
> * search by name all available Vim scripts
> * clean unused plugins up
> * run the above actions in a *single keypress* with interactive mode
>
> Vundle automatically...
>
> * manages the runtime path of your installed scripts
> * regenerates help tags after installing and updating

### How it works?
Normally, plugins and additional configuration files are conventionally stored at `~/.vim` directory. Inside, most plugins are splitted into subdirectories based on the functionality that they provide. These could be things like `autoload`, `plugin`, `colors`, etc. For examples, below is the subdirectories in a conventional `~/.vim` directory:

```
$ ls .vim
autoload  doc  plugin
```

So with this basic structure, files from different plugins are mixed together in differet directories and make it hard for tracking and managing them.

What Vundle does is it creating a top directory, named `bundle`, and inside that, it creates a separate directory tree for each plugin. This means that each plugin will recreate the needed directory structure inside of a subdirectory specific to the plugin, rather than being mixed up with other plugins in separate folders. For examples, here the structure of the `bundle` directory with some installed plugins:

```
$ ls ~/.vim/bundle/
ctrlp.vim  gundo.vim  nerdtree  vim-airline  
vim-airline-themes  vim-startify  Vundle.vim
```

Beside that, Vundle adds an interface in Vim for user to manage the plugins easily with some simple commands.

Now let's jump right in how to get it run!

## Install Vundle
:warning: **NOTICE: This section only shows how to install Vundle on a traditional Linux system (Ubuntu, CentOS, Fedora, etc.). If you're using Windows or MacOS or other, please refer to [offical Wiki guide](https://github.com/VundleVim/Vundle.vim/wiki)**

:warning: **Prequisites**

Installation of Vundle requires Git to clone the repository from Github. If Git is not avalable, you can go to [Github repository] and download the repo as zip file.


## Install plugins with Vundle

## Manage plugins: update, uninstall, etc.

## Conclusion
I'll give other options a chance if I have time for that. For now, Vundle is enough for my need.

[Vundle]:http://github.com/VundleVim/Vundle.vim
[Github repository]:http://github.com/VundleVim/Vundle.vim