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
