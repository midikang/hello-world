Git Configuration Levels
========

The first thing you should do when you get started using Git is to set your configuration options.

Git allows you to set configuration options at three different levels. The default value for Git config is --local.

- --system - These are system-wide configurations. They apply to all users on this computer.
- --global - These are the user level configurations. They only apply to your user account.
- --local - These are the repository level configurations. They only apply to the specific repository where they are set.


Pre-viewing Configuration Settings
========

If you would like to see which config settings have already been added, you can type git config --list. This will automatically read from each of the storage containers for config settings and list them.

Configuring User Name and Email
==================
Go ahead and follow along as we set up our basic configurations. Git uses the config settings for your user name and email address to generate a unique fingerprint for each of the commits you create, so let's set our user name and email address first.

Type git config --global user.name "<your_full_name>" and type git config --global user.email "<your_email>".

Make sure to use the same email address that's associated with your GitHub account.


Configuring Default Editor
========

Next, we will add a default text editor. This is the text editor Git will use when you need to edit things like commit messages or handle merge conflicts.

Typing git config --global core.editor "atom --wait" will tell Git to use the open source atom text editor.

If you don't have atom and would like to use it, you can find it at atom.io. If you would like to use a different editor you can look for instructions (here)[https://help.github.com/articles/associating-text-editors-with-git/].
