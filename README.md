# 100 Days of DevOps with KodeKloud - Days 21 - 30


Greetings! Welcome back. We'll stick with this formatting right now for our challenge. For the next about 15 days, we'll be getting into Git. Now, I'm familiar with using Git Bash, git push and git clone. I don't really use the branch features very often because usually I'm just pushing README.md updates to my GitHub. I'm not a coder (yet at least) so I do plan on learning something new here. Lets get started. 


## Day 30: Git hard reset



## Day 29: Manage Git Pull Requests

Now, we finally get to pull requests. What's a pull request? It's basically just a code review before you actually merge your changes. This is a way for you and someone else on your team to overlook your work to make sure it works. Team work makes the dream work. Lets get started. 

We'll first log into the storage server as user max and we have a cloned repo under our home directory for this user. Max has already pushed his story to remote git repository hosted on Gitea branch story/fox-and-grapes. We need to make sure we see Sarah's story and history of commits by running git log. Validate this author's information. 

We need to create a pull request to merge Max's story/fox-and-grapes branch into the master. We'll use the user tom as the PR review. We need to assign him as the reviewer. We'll do this using the Git Portal UI. 

Okay lets get started. I just noticed you can see the Author of the commits on the `git log` page. Never noticed that. So the changes were already committed and pushed to GitHub. I had to make a new PR request based on this push. Once I did that, if you just got to the PR itself, you'll see on the right hand side you can assign a reviewer. I assigned this to Tom. I logged in as Tom and clicked on my PR notification. I made a comment and clicked git merge. Then I merged the request. That completed the lab.

This wasn't a hard lab but moreso I didn't feel very sure about what I was looking at exactly. It wasn't very clearly stated where to assign reviewers, what constitutes a review, how to actually merge it on the reviewers side, etc. I'll sort out the visuals with AI but I was able to complete this by myself. 

Personal Notes:


## Day 28: Git Cherry Pick

What is git cherry pick? It's exactly what it sounds like. You can pick and choose specific git commits to merge into your master branch instead of committing all the changes that you made. I wasn't aware of this concept so lets give it a try. 

So the command was `git cherry-pick <hash>` which I was able to make this out. I asked Google to make sure my command looked good. The part that AI had to help me out with was the workflow. I needed to switch to the master branch first. Then run my cherry pick command for the specific commit I wanted. Lastly, I had to push my changes using `git push origin master`. I feel like I'm going to forget the order of that soon enough but hey. 

That completed the lab! Pretty easy. 

## Day 27: Git Revert Some Changes

Okay we need to remove the last commit we did. I've never done this before so I'm going to look at the man pages. 

UPDATE: I asked AI to help me understand the question. I didn't know what the lab was really even asking me. SO the point of this lab is to use the `git revert` command. This is not the same as remove or reset. The revert command basically just reverses a commit from your history. You can see your history commits using `git log`. So if you have 2 commits and say you want to reverse the changes of the second commit, using `git revert <commit_name>` is like adding a THIRD commit but the only action done by this third commit is reversing the actions of the second commit. 

So your first commit will be there but after the revert, you'll have 3 commits but only the effects of the first one. I would assume this is more for like, accounting all actions. Instead of just erasing a mistake, it can still be documented by the effects done by the mistake are reversed. Here were the only two commands for this lab:
- git revert --no-commit HEAD
- git commit -m "revert apps"


This was really easy if you knew what to do. Learning experience for me again. 

## Day 26: Git Manage Remotes

For this lab, we need to create a new git remote called dev_news and point it to /opt/xfusioncorp_news.git . Then, we need to copy a file into our master branch, add, commit, and push it to the right remote repo. Now, I'm going to use AI for the first part because origianlly, we're in `/opt/news.git` for the remote repo and we're in `/usr/src/kodekloudrepos/news` for our locally cloned repo. I'm getting a little confused on the remote and locally cloned part so I want to make sure I'm doing that properly. 

Okay first, a remote is a nickname that points to another Git repo. It is not another clone and no additional directories get created. It's just a pointer. Think of it as a saved push/pull destination. Another analogy was say you have your mom's number and your dad's number. You can tell the phone to send this message to your mom and then the phone will find your mom (remote), then find her number (the destination repo), and send her a message (your add and commit). It's just a pointer. It's no data or anything. You're just allowed to use the nickname of it to push your changes somewhere. 

I'll have to let that sink in. Lets get started. I used the man pages to see how to use the `git-remote` command. I followed the example and entered `git remote add dev_news /opt/xfusioncorp_news.git`. For verification, I ran git remote -v and it showed the new remote repo. I then copied the file to the current directory. git status showed that there are some untracked files so I'm going to add and commit them now. First, I did `git add index.html`. Then I ran `git commit -m "Adding the index.html file for deployment"`. Another git status verification check shows there's nothing to commit. Lets push these changes. Since we didn't create any branches and we've been working on the master branch, I ran `git push dev_news master`. 

Everything worked! Okay this made a little more sense. I guess the remotes and pointers just allows you to have a little more granularity and flexibilty when it comes to making changes. Once again, the understanding of the lab took longer than actually doing it. I kind of did the lab myself. Just used the man pages for examples. 

On to the next. 

## Day 25: Git Merge Branches

Okay here's the scenario. We have a repo located at `/opt/demo.git` and a clone of this repo in `/usr/src/kodekloudrepos` on the storage server (ststor01). We need to create a branch called xfusion from the clone repo and then copy the `/tmp/index.html` file on the storage server into the repo. Then, we need to add/commit this file in the new branch and merge back that branch into the master branch. Finally, we need to push the changes to the origin for both of the branches. 

Now, I've never worked with local repos before and while I've done the git init, commit, clone, and push commands for working with my GitHub, I'm not too familiar with this process of merging branches and pushing to local repos. I'm going to ask AI for some help here. This may be more of a "get it under your fingers" lab experience than me doing it from my own knowledge. 

So initially I would go to the /demo/ directory so I did that and saw some hidden files using `ls -la`. I used git branch to make sure I was on the master branch which I was. I then used git branch xfusion to create my branch from the master branch. I'm going to use AI from here on out and find out why each part works. Next, we used the copy command to move the index file over to our branch so `cp /tmp/index.html .`. We used git status to see if there were any changes that needed to be made. Git automatically found the index.html file was untracked so this is a great verification check. 

To add the file, use `git add index.html`. I used another git status and it says we now have changes to be committed. I think this is where I can commit it and make a comment. I went ahead and ran `git commit -m "Added index.html"`. Now, lets switch back to the master branch and use `git merge xfusion` to merge the branches together. After that, you can use `ls -l` and you should be able to see the newly added index.html file! You can also use `git log` to see the changes you've made. 

We still need to push the changes to the origin from both branches (master and xfusion) so first, lets figure out what our origin is. Use `git remote -v` which should show the output of `/opt/demo.git`. Now use the `git push origin master` and `git push origin xfusion` commands to push both branches. You should see the changes getting passed to the origin. 

Thats it for this lab!

Personal Notes:
- Learning moment for me here. Im trying to conceptualize each part of what we did. Okay we can think of Git as having three areas: a working directory, a staging area and a repo. In the working directory, you're editing your files. Git sees the file but doesn't track it. When you do `git add`, you move your file into the staging area and Git tracks it. This is the same as you editing a policy in the FMC and saving the change. Your change is now staged to be deployed. To actually deploy your change like in the FMC, in Git, you have to use `git commit`. The -m flag is for leaving a commit in which you use quotation marks. But this isn't exactly the same as a deployment into prod. Think of git commit as you're saving this verion of the branch.
- When you merge a branch into the master branch, you're bringing the changes your made in the branch into the master branch. So all new files and edited files will now appear in the master branch. This is more like the FMC deployment.
- Lastly, the push to origin part is more like this. When you clone a repo, you're getting a local copy that you can work with and make changes to. If you want those changes on your clone repo to appear in the prod repo, you have to push those changes to the original (origin) repo. That's where `git push origin master` comes from.

So in summary, you have your working directory. You make your changes. You add those changes so those files we be tracked. You then commit those changes to that side branch. You think merge that branch with the master branch for your locally cloned repo. Lastly, you push the changes from your local repo to your prod (remote or origin) repo. 

## Day 24: Git Create Branches
Last one for the day. We need to create a branch from the master branch. That's it that's all. Why is branching important? Might as well ask that while we're here. Branching is the same as forking except think about if this was internal to our organization. Yes, we have permissions to push this code to our overall repo but this also allows us to make changes, the senior engineer can review those changes during a pull request, and then merge or deny the request as they see fit. The branch is where we make our code changes without affecting the main repo and then we merge the branch with the main repo once it's approved. 

I ran into the fatal: detected dubious ownership message again. The CLI wanted me to run the given command to bypass this. Once I did that, I used `git status` and `ls -la` to check if this I was in the repo ( the .git file confirms this ) and it showed me that I was in the branch kodekloud_official. I believe I need to be on the master branch. Use the `git switch master` command to switch to the main branch. Now use the the `git branch xfusioncorp_official` command to make a branch from the master branch. Your branch should have the same files under it as the master branch. 

Lab completed. We'll go over the underlying concept here. Creating a branch doesn't make a copy of the files. Apparently it changes the pointers of the commit or something. My brain is tired. We'll revisit this. 

## Day 23: Fork a Git Repository

Okay we're back! Before we get into the lab, lets figure out what forking is. When you fork a repo, you're creating your own independent copy of the repo. This is different from clone because with clone, you're creating a local working copy of the repo. The fork copy is an entirely new repo that you own. For example, say you're looking at a Microsoft repo. They're obviously not going to let the general public push changes to this repo. If you do git clone, the cloned repo you get is not yours. It's Microsofts. So if you push to it, you'll be denied because you don't have the permissions for it. If you fork the repo, you create your own version of the repo that will most likely go to your own GitHub account. Now, you can make changes and push to it because you own it. 

So for this lab, we needed to log into a fake GitHub account as a user Jon and then fork Sarah's repo. The fork button is located by the Star button to the upper right corner. Once you follow the prompt, the repo should now be located under your user (Jon) as well. 

I pressed submit and got the green check. Nice. Lets keep it rolling. 

## Day 22: Clone Git Repository on Storage Server

For this lab, we need to close a repository (repo) from one location to another location. I'm used to using URLs for the `git clone` command but I think I can figure out how to use it for local repos as well. My thought process is switch to the /usr/src/kodekloudrepos directory and then use the git clone command with the file path of the repo we're trying to close. 

That worked! Very easy. 

## Day 21: Set Up Git Repository on Storage Server

Okay here's our first Git lab! We need to create a Git repository (repo) on the Storage server. We first need to install git and then create a bare repo named `/opt/apps.git/`. 

We'll use `sudo dnf install git -y` to install Git. As far as creating a repo, I'll use the man pages to see how to do that. Usually I create the repo in GitHub first and then push to it. Apparently the man pages were not installed so I had to install the package `man-db`. Going to update it using `sudo mandb` just in case. There's a ton of information in these man pages. I used `man -k init` to get a specific man page on git-init since that was the closest command I could see in the man pages regarding creating a new repo. 

I used `sudo git init /opt/apps.git` to create the new repo and used ls -l to check if the repo was created. You can also use `git status` apparently to check if the repo was created. 

Update: I failed the lab. Apparently it has to be a bare repo. Lets make that happen. Apparently for a bare repo, you need to inlcude the --bare flag so I ran `git init --bare /opt/apps.git`. 

That worked! Now, I don't know the difference between a bare repo and a normal repo but we'll figure that out later. 
