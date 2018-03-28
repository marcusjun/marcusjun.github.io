---
layout: post
title:      "Having trouble with git in the command line?"
date:       2018-03-28 17:12:16 +0000
permalink:  having_trouble_with_git_in_the_command_line
---


I was following the instructions in this lesson: https://learn.co/tracks/full-stack-community-bootcamp/git-and-github/github-remotes/git-remotes-and-github

In the terminal, for step 10, I typed in the command: `git remote add origin git@github.com:marcusjun/*name-of-my-respository*`

I got an error message 

> Permission denied (publickey).
> fatal: Could not read from remote repository.
> 
> Please make sure you have the correct access rights
> and the repository exists.

I think maybe it has to do with my Mac (provided by me employer) and maybe it's security settings?

I tried several times and I was unable to push from my local directory to the github repository.

## What worked for me:

I downloaded github desktop: https://desktop.github.com/ (which is easier to use than the terminal window for me.)

After you create a new repository in github.com, you have the option to do a quick setup and Set up in Desktop.

This opens the github repository in github desktop. Then in github desktop, you go to Repository, Repository Settings, and paste the http from the github quick setup. (I tried pasting the SSH but it didn't work for me.)

After setting this up, I was able to push my local directory through github desktop to the github repository.








