# Git common cheat sheet
## Git Feature Branch Workflow

| Phase | Command | Purpose |
|---|---|---|
| Update `main` | `git switch main` | Switch to local `main` |
|  | `git pull --ff-only origin main` | Update local `main` from GitHub without creating a merge commit |
|  | `git status` | Verify that the working tree is clean |
| Create feature branch | `git switch -c feature/my-feature` | Create and switch to a new local branch |
|  | `git push -u origin HEAD` | Create the branch on `origin` and set the upstream |
| Development | `git status` | Check changed files |
|  | `git add .` | Stage changes |
|  | `git commit -m "Describe the change"` | Create a commit |
|  | `git push` | Push commits to the feature branch on `origin` |
| Feature complete | `git status` | Verify everything is committed |
|  | `git push` | Push the final commits |
| GitHub | **Create Pull Request** | Create PR from feature branch → `main` |
|  | **Merge Pull Request** | Merge the feature into `main` |
|  | **Delete branch** | Delete the remote feature branch on GitHub |
| Back to local repo | `git switch main` | Switch back to local `main` |
|  | `git fetch --prune` | Fetch remote state and remove stale `origin/...` references |
|  | `git pull --ff-only origin main` | Pull the merged changes into local `main` |
|  | `git status` | Verify `main` is up to date and clean |
| Clean up local branch | `git branch -d feature/my-feature` | Delete the local feature branch |
| Final check | `git branch -a` | Show local and remote-tracking branches |

### Quick Reference

```bash
# START
git switch main
git pull --ff-only origin main
git status

git switch -c feature/my-feature
git push -u origin HEAD

# DEVELOPMENT
git status
git add .
git commit -m "Describe the change"
git push

# GITHUB
# Create PR -> Merge -> Delete branch

# CLEAN UP
git switch main
git fetch --prune
git pull --ff-only origin main
git status

git branch -d feature/my-feature
git branch -a
```

> **Rule of thumb:**  
> `git fetch --prune` removes stale **remote-tracking references**, while  
> `git branch -d feature/my-feature` deletes the actual **local branch**.



# Git command list
This file contains the overview list of commands that I want to keep for future reference

### add
git add [filename]  Adds specific file to staging
git add .           Adds all uncommited files (be careful might add env files etc.)
git add all         Same as git add .
git add -a          Same as git add .

### branch
git branch                                              shows current branches
git branch <name of branch>                             created a branch with the given name
git switch -c <new branch name>                         creates new branch
git branch -m [new branch name]                         renames branch into new name
git switch <name of branch>                             switchs to the specified branch
git push --set-upstream origin <branchname>             pushes active branch into upstream named branch.


### branch merging
git merge -m "<message"> <name of branch>               to merge back into branch that is active>
git branch -d <branch name>                             deletes the specified branch
git branch --delete <branch name>                       deletes the specified branch
git checkout <branch name>                              checks out (moves you to edit the specified branch)

### code
code [filename.xxx]                                     Opens up the file in text editior within visual studio code (bash terminal command)

### commit
git commit -m "<enter your message>"
git commit -a -m"<message"> skips the staging area
git commit -m "<message"> --amend updates the commit message with a new oneline

UNSTAGE
see git restore for how to unstage files

### Config
git config --list               Shows the global config settings
git config --global user.email <user email adress>              Adds the user email to global config
git config --global user.name <user name>                       Adds the user name to global config
git config --global init.default branch <branch name>           Adds the branchame as global standard                   


### diff 
git diff [filename]     Difference in files


### fetch
git fetch               downloads all the history from the remote tracking branches, to merge it in just type merge
merge                   merges all downloaded history from remote repo into the local repo. 
pull                    see 3pull more efficient fetches and merges in one go. 


### ignore
.gitignore create a file with the ending .gitignore and edit it. Either specify root filepath to specific file or folder to ignore. can also put in file endings to ignore etc. 


### init
git init                    initializes a git repository

### log
shows all the changes madecd
git log
git log --oneline
git log -p                      shows all the various changess.


### pull                          
git pull                        downloads all the history from the remote tracking branches and automatically merges it locally  
git pull <remote alias> <branch>

### push
git branch -M <name of branch>                  creates a branch with the name
git push -u <name> main                         pushes to alias remote repo the named branch.

git push --all                                  pushes all branches

### status
git status          shows which branch you are on, files that are committed to stagin, unstaged files etc. 

### reset - restores back to previous commit
git reset <hashtag>         # note check the hashtag by using git log --oneline

### rebase
git rebase      opens up editor

### remote
git remote -v                   shows the url that are currently setup with remote repositories
git remote rm <alias of url>    removes the corresponding remote url
git remote rm <remote-url>      removes the corresponding remote url
git remote add <alias> <remote-url to github .gt file> eg. git remote add origin https://www.github.com/username/repositoryname.git


### restore
git restore --staged <filename>    
git restore <filename>          restores deleted file    
git restore --source <ref>      restores a specific revision of the file. By default, the file will be restored to its last committed state. 
git restore --patch             allows you to select individual chunks to restore. 

### rename files 
git mv "<oldfilename"> "<new filename>"

### remove files
git rm "<filename>"
(can also use the file explorer directly)

### review the different commits
git log
git log --oneline

exit view (when you have multiple pages to "page through" and stops and end.)
press q
