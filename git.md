
# git add
_Add changes to staging area and start tracking files_  
_To add all the files_  
```
git add .
```

# Git Bisect
_This is a series of commands to find the commit which introduce a bug, it will checkout different versions and we can test an see if the bug is present_  
**Start**  
```
git bisect start
```
**Identify a commit which was good**
```
git bisect good <git_sha1>
```
**Identify a commit which was bad (no sha assume current)**
```
git bisect bad <git_sha1>
```
_Now git will check out one version and we have to provide feedback that it was good or bad_  
**Return to earlier status**
```
git bisect reset
```

# Git Blame
_Give the information regarding commits which last changed a line in a file_
```
git blame <file_name>
```
```
git blame -L 4,6 <file_name>
```
```
git blame -L 4,+4 <file_name>
```
-s  suppress name and ts  
-e display email instead of name

# Git Branch
**List all the branches**
```
git Branch -a
```
**List all local branch**
```
git branch -v
```
**List all remote branch**
```
git branch -r
```
**Create new branch**
```
git branch <branch-name>
```
**Delete a branch**
```
git branch <branch-name> -d
```
**Force delete a branch**
```
git branch <branch-name> -D
```
**Renaming local branch**
```
git branch -m old-name new-name
```


# Git Checkout
**Switching branch**
```
git checkout <branch_name>
```
Creating new branch
```
git checkout -b <branch_name>
```
Discard changes in working area
```
git checkout <file_name>
```
```
git checkout -- <file_name>
```
```
git checkout -- .
```
Checkout any old commits
```
git checkout <commit_SHA>
```
While merge conflict keep our version
```
git checkout --ours <file_name>
```
While merge conflict keep their version
```
git checkout --theirs <file_name>
```

# Git Cherry-pick
Copy the selected commits from one branch and append them to a different branch  
```
git cherry-pick <commit_sha>
```

-e  edit commit message  
-m parrent number of the merge commit  
-n no commit  

# Git Config
To configure user name and email id
```
git config --global user.name "<First> <Last>"
git config --global user.email "<email_id>"
```
To create Alias for a command
```
git config --global alias.<alias_name> '<git_commad>'
```
Setting merge tool in windows
```
git config --global merge.tool bc3
git config --global mergetool.bc3.cmd "\"c:/program files (x86)/beyond compare 3/BCompare.exe\" "$\LOCAL" "\$REMOTE" "\$BASE" "\$MERGED"
git config --global merge.bc3.trustExitCode true
```

# Git Commit
Saves all the changes 
```
git commit -m"<commit_msg>"
```
Add and commit all changes 
```
git commit -a -m "<commit_msg>"
```
Fixing previous commit with out new commit, re-write history (avoid for public commits) 
```
git commit --amend
```

# Git Clear
Used to remove untracked files 
```
git clear
```
-n to perform dry run  
-f to force delete  
-d to include untracked directory  
-i to perform interactive  

# Git Clone
Get complete project from remote to local maachine 
```
git clone <url>
```
Clone single branch  
```
git clone -b <branch_name> --single-branch <url>
```
 
# Git Diff
Shows exact changes with lines   
```
git diff HEAD~1 HEAD
```

Difference in staged changes 
```
git diff --staged
```

List name of file only which changed 
```
git diff --name-only
```

List the difference of staged files 
```
git diff --cached
```
```
git fetch
```
Download the remote content to your repo. Without changing your code changes   
```
git fetch <remote_name> <branch_name>
```

# git fsck
_Verifies the connectivity and validity of the objects in the database, its helpfull if you are getting error while push, pul or commit._ 
```
git fsck --full
```

Run the above command and remove the file causing fatal and error message, dangling once can be ignored.

# Git Hook
_Runs the script while, it should be present in .git/hooks folder. If new hooks add use chmod 755 to make them executable._  
Commiting workflow  
pre-commit  
prepare-commit-msg  
commit-msg  
post-commit  
Email workflow hooks  
applypatch-msg  
pre-applypatch  
post-applypatch  
Other hooks  
prr-rebase  
post-rewrite  
post-checkout  
 
# Git Init
Initialize the current folder to start tracking with git it creates .git folder
```
git init
```
_ To set main as initial branch _  
```
git init --initial-branch=main
```

# Git Log
Display last two commits
```
git log -2
```
Display history starting from commit_id
```
git log <commit_id>
```
Display the list of commits for the file
```
git log <filename>
```

```
git log --oneline --graph --all --decorate

# Options
--oneline 
--decorate
--graph
--grep=<pattern>
--since='<date>'
--untill='<date>'
--author
--follow ./path/to/filename
```

# Git Merge
Merge changes of branch_name to current branch  
```
git merge <branch_name>
```

Merge the fetched remote content to local working tree
```
git merge origin/<branch_name>
```

# Git Pull
Get new changes from remote repo branch to local repo
```
git pull origin <branch_name>
```
Fetch remote copy and Rebase it into the current branch of local copy
```
git pull --rebase
```

Git pull origin master --allow-unrelated-histories

# Git Push
Send your local branch changes to remote branch
```
git push origin <branch>
```
Deleting remote branch 
```
git push origin -d <branch_name>
```
Renaming remote branch
```
git push origin :old-name new-name
```
Pushing into remote git on filesystem or to push an local branch to remote
```
git push --set-upstream origin master
git push -u origin master
```

Push tags to remote (update as release)
```
git push origin <tag_id>
```
```
git push --tags
```
Delete tag from remote
```
git push origin -d <tag_id>
```
```
git push origin :<tag_id>
```

# Git remote
_Add a new remote repo link to your local repo_ 
```
git remote add <name> <url>
```
_For remote git on file system_ 
```
git remote add origin 'c:/remote.git'
```
_List all remote repo URLs linked to your local repo_ 
```
git remote -v
```
_Update the url of pushing_   
```
git remote set-url origin <url>
```
_Remove origin_   
```
git remote remove origin
```
**_To add multiple push target to a local repo_** 
```
git remote set-url --add --push origin git://original/repo.git
git remote set-url --add --push origin git://another/repo.git
```
_To delete the push target added_ 
```
git remote set-url --delete --push origin git://another/repo.git
```


# Git Rebase
Rebases the current branch onto the base
```
git Rebase <base>
```
Perform interactive Rebase
```
git Rebase -i <base>
```
```
git Rebase --abort
```
```
git Rebase --continue
```

# Git Reflog
_It tracks the head, takes backup for 30 days_ 
```
git reflog
```

# Git Reset (rewrite history)
Undo last commit and keep the file staged
```
git reset --soft HEAD^
``` 
 
 _Unstage a file_ 
```
 git reset HEAD <file_name>
```
_Remove some commits moves changes into staging area not effecting work area_ 
```
 git reset <commit_SHA> --soft
```
```
 git reset --soft
``` 
_Match both working directory and staging area to commit (**changes will be lost**)_   
`--hard`   
_Commit changes are moved to working area_   
`--mixed` 

# Git Revert
Remove old commit and create a new revert commit
```
git revert <commit_sha>
```
-n  don't commit automatically

# Git Rev-parse
Plumbing command primary used for manipulation. Also have massage function to convert one form to another.  
Get the Sha of given revision specifier
```
git rev-parse HEAD
```
```
Git rev-parse --short HEAD
```
--verify to verify if the object is valid git object  
--abbrev-ref to get the branch name  
--git-dir display the abs path of .git directory  

# Git Rm
Remove any tracked file from your repository  
```
git rm <file_name>
```
Restoring deleted file
```
git rev-list -n 1 Head -- filename
```
```
git checkout <commit_sha> -- filename
```

# Git Show

# Git Stash
Temporarily saves the changes made in working directory
```
git stash save "<msg>"
```
List all the stash  
```
git stash list
```
Applys the stashed changes but doesnt delete it
```
git stash apply <stash_id>
```
Will apply the first stash in the list and apply that and drop the stash from list
```
git stash pop
```
Remove the stash 
```
git stash drop <stash_id>
```
Remove all the stash
```
git stash clear
```
-u or --include-untracked include non tracked changes also 

# Git Status
Displays status of staging area and work directory 
```
git status
```

# Git submodule
Add third party library to your project and get updates
```
git submodule add <url>
```
Display status of all submodule
```
git submodule status
```
Update submodule
```
git submodule update
```

# Git switch
_The "switch" command allows you to switch your current HEAD branch. It's relatively new (added in Git v2.23) and provides a simpler alternative to the classic "checkout" command._  
**To switch to other-branch** 
```
git switch <other-branch>
```
**To create a new branch**   
```
git switch -c new-branch
```
 
 
# Git Tag
Adding tag to current commit Id and branch  
```
git tag <tag_id>
```
```
git tag <tag_id> <git_sha1>
```
Annotated tag with desc
```
git tag -a <tag_id> -m"<msg>"
```
List all tag
```
git tag
```
```
git tag -l "v1.*"
```
Delete tag from local
```
git tag -d <tag_id>
```



Operators
Head~1 one commit before head  
Head^1 first parent of head. Usefull when there iss merge.  
Git Diff master..feature  
Git Diffaster...feature shows difference starting from last common commit  
