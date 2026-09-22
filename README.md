# 100 Days of DevOps with KodeKloud - Days 21 - 30


Greetings! Welcome back. We'll stick with this formatting right now for our challenge. For the next about 15 days, we'll be getting into Git. Now, I'm familiar with using Git Bash, git push and git clone. I don't really use the branch features very often because usually I'm just pushing README.md updates to my GitHub. I'm not a coder (yet at least) so I do plan on learning something new here. Lets get started. 


## Day 30: Git hard reset



## Day 29: Manage Git Pull Requests



## Day 28: Git Cherry Pick



## Day 27: Git Revert Some Changes



## Day 26: Git Manage Remotes



## Day 25: Git Merge Branches



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
