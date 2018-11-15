# Using git

Notes from [here](https://www.youtube.com/watch?v=HVsySz-h9r4).

[This]('https://nvie.com/posts/a-successful-git-branching-model/') workflow is good also.

## Info and config

Git is a distributed version control system: 

- Everyone has their own local version of the remote repository

Config  

- Set name and username 

Help  

`git config —help`

## Tracking local projects

git init

Files we don't want tracked create a .gitignore file
`touch .gitignore`

Add files you want git to ignore. Can use wildcards. E.g.

```
.DS_Store
.project
*.css
```

States:

- working directory (untracked, modified files, listed in git status)
- taging area (organise what we want to be committed, pick and choose)
- git directory

Add untracked files to staging area: `git add -A`
Add individually:  `git add file`

Remove from staging area: `git reset file`  
Remove everything from staging area: `git reset`

Commit: `git commit -m "message"`
If you check status now can see have a clean 
Check commits: `git log`

Now we are successfully tracking a local project


## Track existing remote project

E.g. company has remote repository you want to develop on

Clone files from a remote to current directory: `git clone <url> .`

List repo information: `git remote -v`  
List all branches in repo (remote and local): `git branch -a`

### Pushing changes
Show changes you've made: `git diff`  
Add everything to staging directory
Commit the changes with message  
Now changes have been committed locally

If any changes were made to the repository since we cloned it, we can pull in any other changes: `git pull origin master`  

Can now push: `git push origin master`

## Workflow

### branches

Git master branch isn't how you should be using day-to-day.

Create branch for desired feature, and then work on that branch: `git branch <name>`  
To see all the branches and show the active one: `git branch`

To work on a particular branch need to checkout: `git checkout <name>`  

Then run `git branch` to see current one.  

Can make changes, and add and commit to local branch, but it won't have changed the master.

To push `git push -u origin <name>`  
The `-u` tells git we want to associate the branch with our local place, so in future can do simply `git push` and `git pull`. 

Can now run `git branch -a` again to see all of our branches, to see local branches, and also remote repo branches.

### merge with the master

Switch to the master   
Pull down master in case changes were made   
Check which branches have been merged so far  
Merge changes into the master  
Push changes to remote master  


```
git checkout master
git pull origin master
git branch --merged
git merge <name>
git push origin master
```

Now it's done we can delete the branch. 
Check to see if changes have been merged in the master, the new one should show up.  
Delete it locally
Check if branch still in remote
Delete it from repo


```
git branch --merged
git branch -d <name>
git branch -a
git push origin --delete <name>
```

### workflow summary
To work on new function

- branch
- checkout
- make changes
- check status
- add to staging
- commit changes
- push to branch to remote repo
- checkout to master
- pull in changes from master
- merge with master
- push changes to master
- delete branch
