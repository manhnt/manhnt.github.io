---
layout: post
title: Vundle for beginner - Vim plugins manager
categories: vim
---

# Vim, plugins and plugin manager
Well, if you're reading this article, then I assume that you already know what Vim editor is. So let me skip the introduce part.

One key feature that makes the power of Vim is the plugin system. Vim let you extends, enhance its power, abilities (and complexities) through the plugins that you can install.

You may have installed some plugins by hand, manually. That's what I did the first time I installed a plugin: download the plugin, untar, put the files in some specified directories, even need to run some additional commands to make it work.

Maybe that method is easy for you. But the problem is we often don't install just 1 or 2 plugin. There are thousand of plugins, and you may love to install dozens of them. Installing all of them manually is a very tedious work. Let imagine you have a dozen plugins that you use them every day. And one day you get a new machine where none of your favourite plugins is there. It could be painful & boring task to have to manually download and install all of them by hand.

That's why we should use a plugin manager to automate the process of setting up our plugins, and manage them for us. By "manage", I mean the tasks of tracking, updating, uninstalling, etc. the plugins that were installed.

There are many options for you to choose a plugin manager for Vim. Take a quick search on Google and you will see some names like Vundle, Pathogen, vim-plug, etc.. In this specific post, I will talk about Vundle. Why? Because I haven't used the others :innocent: 

# What is Vundle?
[Vundle] is a Vim plugin that, well, manages other plugins (and even itself). From the [introduction](https://github.com/VundleVim/Vundle.vim/blob/master/README.md):

Vundle allows you to...

* keep track of and configure your plugins right in the `.vimrc`
* install configured plugins (a.k.a. scripts/bundle)
* update configured plugins
* search by name all available Vim scripts
* clean unused plugins up
* run the above actions in a *single keypress* with interactive mode

Vundle automatically...

* manages the runtime path of your installed scripts
* regenerates help tags after installing and updating

## How it works?
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

# Install Vundle
**NOTICE: This section only shows how to install Vundle on a traditional Linux system (Ubuntu, CentOS, Fedora, etc.). If you're using Windows or MacOS or other, please refer to [offical Wiki guide](https://github.com/VundleVim/Vundle.vim/wiki)**

## Prequisites

Installation of Vundle requires Git to clone the repository from Github. If Git
is not avalable, you can go to [Github repository] and download the repo as zip file.

## Download Vundle
Fire up the command line and `git clone` Vundle repository from GitHub

```
$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

Notice that we store Vundle in `~/.vim/bundle/Vundle.vim` directory.

## Configure Vundle
We need to configure few things before Vundle can work properly. First, we need
to turn off compatible mode of vim with vi. It's Vundle's requirement. Some
other configuration must also be set before Vundle config. Put this at the top
of your `~/.vimrc` file.

```
set nocompatible              " be iMproved, required
filetype off                  " required <<========== We can turn it on later

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" <============================================>
" Specify the plugins you want to install here.
" We'll come on that later
" <============================================>
" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
" Put the rest of your .vimrc file here
```

As you see, we need to make Vundle manage itself by `Plugin 'VundleVim/Vundle.vim'` line.

Now, we can start adding plugins that we wish to install & manage. The cool thing
about Vundle is that it supports to download or link the plugins from various
source: online Github repo, [vim scripts], other remote/local git repositories. You
just need to specify the plugins with the correct syntax format that Vundle supports.
The following are some examples (put this in the specific section which was marked out above):

```
" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
Plugin 'ascenator/L9', {'name': 'newL9'}
```

That should be enough for Vundle knows how to locate the plugins.

# Install plugins with Vundle
Now that you've told Vundle which plugins you wish to install, there's still one more
(very simple) step that you need to do: tell Vundle to *really install* those plugins.
You can do this by simply open `vim` and run command `:PluginInstall`. Vundle will
start processing and installing the plugins one by one.

That's it! All plugins are now installed. In the next section, we'll see how to
perform management tasks for the plugins, such as update, uninstall, etc.

# Manage plugins

## Update plugins
If you wish to update the plugins to their latest version, just run this
command in vim:

```
:PluginUpdate
```

or

```
:PluginInstall!
```

The second command will reinstall all of the plugins.

## Install new plugins
You can search for plugins by name with command `:PluginSearch`. For example,
if you want to search for an 'foo' plugin, you can type:

```
:PluginSearch foo
```

Vundle will search Vim Scripts site for matching plugins. The result is
displayed in a new window. With the above command, the result will be something
like:

```
"Keymap: i - Install plugin; c - Cleanup; s - Search; R - Reload list
"Search results for: foo
Plugin 'MarkdownFootnotes'
Plugin 'VimFootnotes'
Plugin 'foo.vim'
```

To install a plugin, move to the correct line and press 'i'. This will download
plugin, but you still need to update your `.vimrc` to make it work. For
example, if you want to install VimFootnotes, you press 'i' at its line, and
then add a new plugin line in your `.vimrc`:

```
...
Plugin 'VimFootnotes'
...
```

Now the new plugins should be installed and works. Another way to install a new
plugin is, of course, similar to what we do when first configure Vundle: adding
a new plugin line for the plugin in `.vimrc` and then run `:PluginInstall`.

## Uninstall plugins
At some time, you may want to take a look what plugins you've install on you
system. The `:PluginList` command will open a new windows in which list up all
the plugins installed:

```
" My Plugins
Plugin 'VundleVim/Vundle.vim'
Plugin 'vim-airline/vim-airline'
Plugin 'vim-airline/vim-airline-themes'
```

If you wish to uninstall one of theme, just move the cursor to correct line,
and press `D`. After that, remove the corresponding plugin line in `.vimrc`
file to completely uninstall the plugin from the system.

Another method for uninstalling is to remove the plugin line in `.vimrc` first,
then run command `:PluginClean`. This command will remove all plugins that no
longered present in your `.vimrc` but still present the bundle directory.

# Conclusion
Now you have known the basic usage of Vundle to manage your plugins list. This
should be enough for most of your common need. After using it for some time, I
think you will appreciate, like I do, the simplicity that Vundle offers us in managing Vim
plugins, especially when you use many plugins or want quick trial of some new
cool plugins.

There're  many other options for plugin manager in Vim that I haven't tried. I'll give other
options a chance if I have time for that. For now, Vundle is enough for my need.

[Vundle]:http://github.com/VundleVim/Vundle.vim
[Github repository]:http://github.com/VundleVim/Vundle.vim
[vim scripts]:http://www.vim.org/scripts/
