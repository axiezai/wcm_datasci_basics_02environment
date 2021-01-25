---
title: "Assignment"
teaching: "0"
exercises: "40"
---

## Assignment

### Part 1: Set-up your shell

#### Dotfiles

Let’s get you up to speed with dotfiles.

 1. Using the terminal, create a folder for your dotfiles in your home directory (`~`), we will learn how to version control and publish this folder in the next class.
 2. Add a configuration for at least one program, e.g. your shell, with some customization (to start off, it can be something as simple as customizing your shell prompt by setting $PS1).
 3. Set up a method to install your dotfiles quickly (and without manual effort) on a new machine. This can be as simple as a shell script that calls `ln -s` for each file, or you could use a specialized utility.
 4. Create a back up folder for your current dotfiles and test your installation script.
 5. Migrate all of your current tool configurations to your dotfiles repository.

#### Terminal Multiplexer
 1. Follow this tmux tutorial and then learn how to do some basic customizations following these steps.
 2. Your customized `.tmux.conf` dotfile should also be placed in your dotfiles folder.

#### Aliases
If you are using bash, you can place your aliases in `.bashrc` file, or create a separate `.bash_aliases` dotfile and `source` the file in your `.bashrc` workflow. With `zsh`, your aliases are placed in `.zshrc`.

 1. Create an alias `dc` that resolves to `cd` for when you type it wrongly.

 2. Run `history | awk '{$1="";print substr($0,2)}' | sort | uniq -c | sort -n | tail -n 10` to get your top 10 most used commands and consider writing shorter aliases for them. Note: this works for Bash; if you’re using ZSH, use history 1 instead of just history. You don't have to write one for all 10, but consider the most useful ones for you. 

### Part 2: Tools and Scripting
 
 1. Read [`man ls`](https://www.man7.org/linux/man-pages/man1/ls.1.html) and write an `ls` command that lists files in the following manner

    - Includes all files, including hidden files
    - Sizes are listed in human readable format (e.g. 454M instead of 454279954)
    - Files are ordered by recency
    Output is colorized

    A sample output would look like this

    ~~~
     -rw-r--r--   1 user group 1.1M Jan 14 09:53 baz
     drwxr-xr-x   5 user group  160 Jan 14 09:53 .
     -rw-r--r--   1 user group  514 Jan 14 06:42 bar
     -rw-r--r--   1 user group 106M Jan 13 12:12 foo
     drwx------+ 47 user group 1.5K Jan 12 18:08 ..
     ~~~
     {: .bash}

 2. Write bash functions `marco` and `polo` that do the following. Whenever you execute `marco` the current working directory should be saved in some manner, then when you execute `polo`, no matter what directory you are in, `polo` should `cd` you back to the directory where you executed marco. For ease of debugging you can write the code in a file `marco.sh` and (re)load the definitions to your shell by executing `source marco.sh`.

 3. Say you have a command that fails rarely. In order to debug it you need to capture its output but it can be time consuming to get a failure run. Write a bash script that runs the following script until it fails and captures its standard output and error streams to files and prints everything at the end. Bonus points if you can also report how many runs it took for the script to fail.

    ~~~
    #!/usr/bin/env bash

    n=$(( RANDOM % 100 ))

    if [[ n -eq 42 ]]; then
        echo "Something went wrong"
        >&2 echo "The error was using magic numbers"
        exit 1
    fi

    echo "Everything went according to plan"
    ~~~
    {: .bash}

