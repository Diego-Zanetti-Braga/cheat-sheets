
## Important informations
- "index state" is the same as the staging area


## Iniciate a git repository

- Open git bash
- Go to the folder where you want to initiate the git repository and use the following command
````
$ git init
````
- Check if this is alredy a git repository
````
$ git status
````
## Commit

- First, stage the files that you want to stage
````
$ git add <file_name.txt>
````
- or stage all changes
````
$ git add .
````
- Commiting
````
$ git commit -m "you commit message here"
````
- Commiting and adding all files that have already been staged at least once before
````
$ git commit -am "you commit message here" 
````
## Branching

- See all branches available
````
$ git branch
````
- See all remote branches
````
$ git branch -r
````
NOTE: Sometimes when you clone a repo, you can't  see all the branches so you have to use the parameter ````-r````.
- Swicth branches
````
$ git switch <branch_that_you_want_to_go>
````
NOTE: the command above works even for remote branches connected to the repo.
or the old way
````
$ git checkout <branch_that_you_want_to_go>
````
or the old way if the branch is a remote branch
````
$ git checkout --track origin/<branch_that_you_want_to_go>
````
- Switch to origin branch (with dettached head)
````
$ git checkout <origin/main>
````
NOTE: Usually the name of the origin branch will be origin/main but sometimes that can change. To be sure about the origin brach name execute ````git branch -r````
- Switch the the previous branch you were in before
````
$ git switch -
````
- Create a new branch based on another one
````
$ git switch <branch_you_want_to_copy>
````
````
$ git switch -c <branch_you_want_to_create>
````
or
````
$ git checkout -b <branch_you_want_to_create>
````
- Delete a branch
````
$ git branch -d <branch_name>
````
or
````
$ git branch -D <branch_name> (if it is a branch that has never been merged to any other branch)
````

## Merging

- Go to the branch that you want to receive the changes of the other branch
````
$ git merge <branch_with_the_changes>
````

## Diff

- See the differences between the Working Area (or WIP: Work In Progress) and steged files
````
$ git diff
````
- See the differences between the staging and working area and the last commit
````
$ git diff head <optional: file_name if you want to diff a specific file>
````
- See the differences between staging area and the last commit
````
$ git diff --staged <optional: file_name if you want to diff a specific file>
````
````
$ git diff --cached <optional: file_name if you want to diff a specific file>
````
- Compare files between two different branches
````
$ git diff branch-a..branch-b
````
or
````
$ git diff branch-a branch-b
````
- To compare a specific file between branches
````
$ git diff branch-a..branch-b -- file_name.txt
````

- Compare files between two different commits
````
$ git diff ce4175d..811a471
````
or
````
$ git diff ce4175d  811a471
````
- Compare the current HEAD with the previous HEAD
````
$ git diff head..head~1
````
or just
````
$ git diff head~1 (this code is the same as "git diff head~1..head", it just switches the order)
````
## Stashing
- Stash (hide/save) WIP (staged and unstaged) so you can move branches without the need to commit
````
$ git stash ("git stash save" is the same)
````
- Unstash (apply stashed changes) and drop the changes of the stash (if there is more then one stash it will consider the last one)
````
$ git stash pop
````
- Unstash (apply stashed changes) and keep the changes of the stash in memory (if there is more then one stash it will consider the last one)
````
$ git stash apply
````
- List os the stashes that you have in memory
````
$ git stash list
````
- Apply a specific stash version
````
$ git stash apply stash@{1}
````
(the versions of stash will have an alias that look like this: "stash@{1}", "stash@{2}", etc..)

- Drop a specific stash
````
$ git stash drop stash@{1}
````
- Drop all stashes
````
$ git stash clear
````
## Time Travel (with dettached head)

- Come back to a previous commit state by coping it's commit hash (entirerly or just the first 7 characters) and using the code below.
````
$ git checkout 296j254
````
or go to the previous commit using HEAD\~1, HEAD\~2, etc
````
$ git checkout HEAD~1
````
When it is done you are not in any branch.
You can come back to any branch by switching or create a new branch with ```` $ git switch -c <new_branch_name>```` using this old commit as a stating point.

- Discart everything that you did after the last commit (staged and unstaged changes)
````
$ git checkout head <file_name>
````

## Time traveling (without dettached head)
- Get the state of the last commit for a file
````
$ git restore <file_name>
````
- Get the state of a specific commit for a file
````
$ git restore --source <HEAD~1,2,3 etc or commit_hash> <file_name>
````
## Unstaging files
````
$ git restore --staged <file_name>
````

## Remove last X commits from history
- Makes HEAD point to a specifit commit, erases the history of the commits that came after this one, but does't erase the changes in the WIP area.
````
$ git reset <commit hash>
````
Using this stragegy you can create a new branch to use this changes that are still in the WIP using ````$ git switch -c new_branch_name````
Or you can return to a specific commit and also remove all work done in the WIP area by using the parameter --hard:
````
$ git reset --hard <commit hash>
````
## Reverting a commit (but still keep it in the history)
- In order to ignore the changes that you've done in a commit, but still keep it in the history you should use revert
````
$ git revert <commit hash>
````

It will create a new commit ignoring all changes done by the commit you referenced in the command.

## Set the Remote Repository
Note: If the repo was cloned, it already has a remote file set up.
- To check if there is already a remote repository set up
````
$ git remote -v
````
- Set a remote repository for the project folder
````
$ git remote add origin <url of the remote repo>
````

## Pushing work to a remote repo
- Push work to a repository with the same name
````
$ git push origin <branch_name>
````
- Push work to a repository with a different name
````
$ git push origin <local_branch_name>:<remote_branch_name>
````
- If you want to push your current branch only by using the code ````$ git push```` you have to set the upstream branch of origin for that branch using the code below
````
$ git push -u origin <branch_name>
````

## Rename a branch (while in it)
````
$ git branch -M <nem_branch_name>
````

## Fetching and Pulling work to from the remote repo
- Fetch will update your remote-tracking branches with the remote changes, but will not change anything in your current work (is safe to do anytime)
````
$ git fetch origin <branch_name>
````
or just (when you have only one origin and you are in the current branch you want to fetch)
````
$ git fetch
````
- Pull will update your current work space with the remote changes, (it can result in merge conflicts)
````
$ git pull origin <branch_name>
````
or just (when you have only one origin and you are in the current branch you want to pull)
````
$ git pull
````

## Rebase
- Rebase will rewrite the commits that you have in your current branch. the hashes wil literaly chance, so be careful.
- It is used to clean up your history when you want to "forget" all the merges (pulling, not pushing, from master to feature-branch) that you had to do throughout your development
While in your development branch:
````
$ git rebase master
````
To edit the commits use the parameters:  ````-i HEAD~[number of commits back you want to be shown on the screen]````
````
$ git rebase -i HEAD~9
````
Notes: The commits view ir ordered with the oldest up and newest down, the opposite of git log view. All the commits after the one you change (including itself) will have the hash changed.
Then you edit the words that preced the commit hashes. 

- pick: Is the default word and is used to keep that commit the way it is.
- reword: Used to rename the commit.
- fixup: Used to merge the commit with the one righ above it. The commit above will remain but will have the changes applyed to the commit you used fixup.

Once youre done, you close the editor to proceed the changes
