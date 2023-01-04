
# Git Add
_Add changes to staging area and start tracking files_

# Git Bisect
_This is a series of commands to find the commit which introduce a bug, it will checkout different versions and we can test an see if the bug is present_\
**Start**\
`Git Bisect start`\
**Identify a commit which was good**\
`Git Bisect good <git_sha1>`\
**Identify a commit which was bad (no sha assume current)**\
`Git Bisect bad <git_sha1>`\
_Now git will check out one version and we have to provide feedback that it was good or bad_\
**Return to earlier status**\
`Git Bisect reset`\

# Git Blame
_Give the information regarding commits which last changed a line in a file_\
`Git Blame <file_name>`\
`Git Blame -L 4,6 <file_name>`\
`Git Blame -L 4,+4 <file_name>`\\
-s  suppress name and ts\
-e display email instead of name\

# Git Branch
**List all the branches**\
Git Branch -a\
**List all local branch**\
Git Branch -v\
**List all remote branch**\
Git Branch -r\
**Create new branch**\
Git Branch <branch-name>\
**Delete a branch**\
Git Branch <branch-name> -d\
**Force delete a branch**\
Git Branch <branch-name> -D\
**Renaming local branch**\
Git branch -m old-name new-name\


# Git Checkout
**Switching branch**\
Git checkout <branch_name>\
Creating new branch\
Git checkout -b <branch_name>\
Discard changes in working area\
Git checkout <file_name>\
Git checkout -- <file_name>\
Git checkout -- .\
Checkout any old commits\
Git checkout <commit_SHA> \
While merge conflict keep our version\
Git checkout --ours <file_name> \
While merge conflict keep their version\
Git checkout --theirs <file_name> \

# Git Cherry-pick
Copy the selected commits from one branch and append them to a different branch\
Git Cherry-pick <commit_sha> \

-e  edit commit message\
-m parrent number of the merge commit\
-n no commit\

# Git Config
To configure user name and email id\
Git Config --global user.name "<First> <Last>"\
Git Config --global user.email "<email_id>"\
To create Alias for a command\
Git Config --global alias.<alias_name> '<git_commad>'\
Setting merge tool in windows\
git config --global merge.tool bc3\
git config --global mergetool.bc3.cmd "\"c:/program files (x86)/beyond compare 3/BCompare.exe\" "$\LOCAL" "\$REMOTE" "\$BASE" "\$MERGED"\
git config --global merge.bc3.trustExitCode true\

# Git Commit
Saves all the changes \
Git Commit -m"<commit_msg>" \
Add and commit all changes \
Git Commit -a -m "<commit_msg>" \
Fixing previous commit with out new commit, re-write history (avoid for public commits) \
Git Commit --amend \

# Git Clear
Used to remove untracked files \
Git clear \
-n to perform dry run \
-f to force delete \
-d to include untracked directory \
-i to perform interactive \

# Git Clone
Get complete project from remote to local maachine \
Git clone <url> \
Clone single branch  \
Git clone -b <branch_name> --single-branch <url> \
 
# Git Diff
Shows exact changes with lines \
Git Diff HEAD~1 HEAD \

Difference in staged changes \
Git Diff --staged \

List name of file only which changed \
Git Diff --name-only \

List the difference of staged files \
`Git Diff --cached` \
`Git fetch` \
Download the remote content to your repo. Without changing your code changes \
`Git fetch <remote_name> <branch_name>` \

# Git Hook
_Runs the script while, it should be present in .git/hooks folder. If new hooks add use chmod 755 to make them executable._ \
Commiting workflow \
pre-commit \
prepare-commit-msg\
commit-msg\
post-commit\
Email workflow hooks\
applypatch-msg\
pre-applypatch\
post-applypatch\
Other hooks\
prr-rebase\
post-rewrite\
post-checkout\
Git Init\
Initialize the current folder to start tracking with git it creates .git folder\

# Git Log
Display last two commits\
Git log -2\
Display history starting from commit_id\
Git log <commit_id> \
Display the list of commits for the file\
Git log <filename> \

`Git log --oneline --graph --all --decorate` \
--oneline \
--decorate\
--graph\
--grep=<pattern>\
--since='<date>'\
--untill='<date>'\
--author\
--follow ./path/to/filename\

# Git Merge
Merge changes of one branch to other\
Git Merge <branch_name>\

Merge the fetched remote content to local working tree\
Git Merge Origin/<branch_name>\

# Git Pull
Get new changes from remote repo branch to local repo\
Git pull origin <branch_name> \
Fetch remote copy and Rebase it into the current branch of local copy\
Git pull --rebase\

Git pull origin master --allow-unrelated-histories\

# Git Push
Send your local branch changes to remote branch\
Git push origin <branch> \
Deleting remote branch \
Git push origin -d <branch_name> \
Renaming remote branch\
Git push origin :old-name new-name\
Pushing into remote git on filesystem\
Git push --set-upstream origin master\
Push tags to remote (update as release)\
Git push origin <tag_id> \
Git push --tags\
Delete tag from remote\
Git push origin -d <tag_id> \
Git push origin :<tag_id> \

# Git remote
_Add a new remote repo link to your local repo_ \
`git remote add <name> <url>` \
_For remote git on file system_ \
`git remote add origin 'c:/remote.git'` \
_List all remote repo URLs linked to your local repo_ \
`git remote -v` \
_Update the url of pushing_ \
`git remote set-url origin <url>` \
_Remove origin_ \
`git remote remove origin` \
**_To add multiple push target to a local repo_** \
`git remote set-url --add --push origin git://original/repo.git` \
`git remote set-url --add --push origin git://another/repo.git` \
 _To delete the push target added_ \
 `git remote set-url --delete --push origin git://another/repo.git` 


# Git Rebase
Rebases the current branch onto the base\
Git Rebase <base> \
Perform interactive Rebase\
Git Rebase -i <base> \
Git Rebase --abort\
Git Rebase --continue\

# Git Reflog
It tracks the head, takes backup for 30 days\
Git reflog\

# Git Reset (rewrite history)
Unstage a file\
Git Reset HEAD <file_name> \
Remove some commits moves changes into staging area not effecting work area\
Git Reset <commit_SHA> --soft\
Match both working directory and staging area to commit (changes will be lost)\
--hard\
Commit changes are moved to working area\
--mixed\

# Git Revert
Remove old commit and create a new revert commit\
Git Revert <commit_sha> \
-n  don't commit automatically\

# Git Rev-parse
Plumbing command primary used for manipulation. Also have massage function to convert one form to another.\
Get the Sha of given revision specifier\
Git Rev-parse HEAD\
Git Rev-parse --short HEAD\
--verify to verify if the object is valid git object\
--abbrev-ref to get the branch name\
--git-dir display the abs path of .git directory\

# Git Rm
Remove any tracked file from your repository\
Git Rm <file_name> \
Restoring deleted file\
Git Rev-list -n 1 Head -- filename\
Git checkout <commit_sha> -- filename\

# Git Show

# Git Stash
Temporarily saves the changes made in working directory\
Git Stash save "<msg>"\
List all the stash\
Git Stash list\
Applys the stashed changes but doesnt delete it\
Git Stash apply <stash_id> \
Will apply the first stash in the list and apply that and drop the stash from list\
Git Stash pop\
Remove the stash \
Git Stash drop <stash_id> \
Remove all the stash\
Git Stash clear\
-u or --include-untracked include non tracked changes also \

# Git Status
Displays status of staging area and work directory \

# Git submodule
Add third party library to your project and get updates\
Git submodule add <url> \
Display status of all submodule\
Git submodule status\
Update submodule\
Git submodule update\

# Git switch
_The "switch" command allows you to switch your current HEAD branch. It's relatively new (added in Git v2.23) and provides a simpler alternative to the classic "checkout" command._ \
**To switch to other-branch** \
`git switch <other-branch>` \
**To create a new branch** \
`git switch -c new-branch` \
 
 
# Git Tag
Adding tag to current commit Id and branch\
Git tag <tag_id> \
Git tag <tag_id> <git_sha1> \
Annotated tag with desc\
Git tag -a <tag_id> -m"<msg>"\
List all tag\
Git tag\
Git tag -l "v1.*"\
Delete tag from local\
Git tag -d <tag_id> \



Operators
Head~1 one commit before head
Head^1 first parent of head. Usefull when there iss merge.
Git Diff master..feature
Git Diffaster...feature shows difference starting from last common commit
