## Basic Unix commands to use git bash
- Enter a folder
>> cd <folder_name>

- Go to one folder up
>> cd ..

- Go to the root folder
>> cd ~

- Make a new folder
>> mkdir <folder_vame>

- Create a new file
>> touch <file_name.extension>

## Iniciate a git repository

- Open git bash
- Go to the folder where you want to initiate the git repository and use the following command
>> git init

- Check if this is alredy a git repository
>> git status

## Commit

- First, stage the files that you want to stage
>> git add <file_name.txt>

- or stage all changes
>> git add .

## Branching

- See all branches available
>> git branch

- Swicth branches
>> git switch <branch_that_you_want_to_go>
or
>> git checkout <branch_that_you_want_to_go>

- Create a new branch based on another one
>> git switch <branch_you_want_to_copy>
>> git switch -c <branch_you_want_to_create>
or
>> git checkout -b <branch_you_want_to_create>

## Merging

- Go to the branch that you want to receive the changes of the other branch
>> git merge <branch_with_the_changes>


## Diff

- See the differences between the Working Area (or WIP: Work In Progress) and steged files
>> git diff

- See the differences between the staging and working area and the last commit
>> git diff head

- See the differences between staging area and the last commit
>> git diff --staged
