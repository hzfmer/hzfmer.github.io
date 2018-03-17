---
layout: post
title: What happens in opening a shell 
date: 2018-03-16 23:05
tag: 计算机入门
---

## What happens?
If `zsh` is the login shell:

    zsh -xl 2>/tmp/file.log

With `Bash`:

    PS4='+$BASH_SOURCE> ' BASH_XTRACEFD=7 bash -xl 7>/tmp/file.log

This will simulate a login shell and things like environment variables can be found here. If not, they are set before, e.g. in `~/.ssh/environment`. Then `find /etc -type f -exec grep -F THE_VAR {} +` may help.

## Some places to look

### **System wide**
* `/etc/environment`: specially meant for environmental variables
* `/etc/env.d/\*`: environment variables, split in multiple files
* `/etc/profile`: all types of initialization scripts
* `/etc/profile.d/\*`: initialization scripts
* `/etc/bashrc`: meant for functions and aliases

### **User specific**
* `~/.bash_profile`: initialization for login (bash-)shells
* `~/.bashrc`: initialization for all interactive (bash-)shells
* `~/profile`: used for all shells
* `~/zshrc`: for non-bash shells

> Gathered from [stackexchange](https://unix.stackexchange.com/questions/813/how-to-determine-where-an-environment-variable-came-from)
