# 100 Days of DevOps with KodeKloud - Days 21 - 30


Greetings! Welcome back. We'll stick with this formatting right now for our challenge. For the next about 15 days, we'll be getting into Git. Now, I'm familiar with using Git Bash, git push and git clone. I don't really use the branch features very often because usually I'm just pushing README.md updates to my GitHub. I'm not a coder (yet at least) so I do plan on learning something new here. Lets get started. 


## Day 30: Git hard reset



## Day 29: Manage Git Pull Requests



## Day 28: Git Cherry Pick



## Day 27: Git Revert Some Changes



## Day 26: Git Manage Remotes



## Day 25: Git Merge Branches



## Day 24: Git Create Branches



## Day 23: Fork a Git Repository



## Day 22: Clone Git Repository on Storage Server



## Day 21: Set Up Git Repository on Storage Server

Okay here's our first Git lab! We need to create a Git repository (repo) on the Storage server. We first need to install git and then create a bare repo named `/opt/apps.git/`. 

We'll use `sudo dnf install git -y` to install Git. As far as creating a repo, I'll use the man pages to see how to do that. Usually I create the repo in GitHub first and then push to it. Apparently the man pages were not installed so I had to install the package `man-db`. Going to update it using `sudo mandb` just in case. There's a ton of information in these man pages. I used `man -k init` to get a specific man page on git-init since that was the closest command I could see in the man pages regarding creating a new repo. 

I used `sudo git init /opt/apps.git` to create the new repo and used ls -l to check if the repo was created. You can also use `git status` apparently to check if the repo was created. 

Update: I failed the lab. Apparently it has to be a bare repo. Lets make that happen. Apparently for a bare repo, you need to inlcude the --bare flag so I ran `git init --bare /opt/apps.git`. 

That worked! Now, I don't know the difference between a bare repo and a normal repo but we'll figure that out later. 
