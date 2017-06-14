# git-cheats
## GIT Cheats

1--to install angular-cli-ghpages package (used for building and displaying your webpage on github):
* npm i -g angular-cli-ghpages

!!!You're only able to use the angular-cli-ghpages CLI if you have a /dist folder. If you do, you can then run: 
* ngh  

2--to build the Angular project 
* ng build --prod 

3--to build the angular project for github  
* ng build --prod --base-href https://alextelespanwork.github.io/my-cool-proj/

## To create a new repository:
1--login to your github.com account and create a new repository for your Angular project.

2--then follow the commands similar to the ones below:
* git init
* git add README.md
* git commit -m "first commit"
* git remote add origin https://github.com/alextelespanwork/my-cool-proj.git
* git push -u origin master

## GeneralCommands:  
1--check for changes
* git status
* git status -s  (dsiplays less information prefixed with the change)

2--to add files to the staging repo 
* git add <filename> (to add one file)
* git add . (to add all files)

3--commit the changes
* git commit -m "Your message about the commit"

4--to discard the changes
* git checkout --(filename)

5--to push on that branch
* git push -u origin master

6--undoing changes (command to backtrack)
* git revert <hash code number> 

7--to pull when working on the master branch
* git pull origin master 

8--command to see all new commits
* git log

9--to make your local files changed to be like they were at a specific commit, but leave your history etc. the same. (does not touch the index file nor the working tree at all (but resets the head to <commit>, just like all modes do). This leaves all your changed files "Changes to be committed", as git status would put it.)
* git reset --soft c14809fafb08b9e96ff2879999ba8c807d10fb07

10--to make your local code and local history be just like it was at that commit. But then if you wanted to push this to someone else who has the new history, it would fail.
* git reset --hard c14809fa

11--
* git reset c14809fafb08b9e96ff2879999ba8c807d10fb07

## New Branch:
1--create a branch (git will move you to that branch, off of the master branch)
* git checkout -b <my branch name>

2--to confirm that your branch was created:
* git branch

3--to switch branches back to the master branch. 
* git checkout master 

## Various ways to remove local Git changes:
- Type 1. Staged Tracked files (Those that are moved to staging area/ Added to index)
- Type 2. Unstaged Tracked files (modified files)
- Type 3. Unstaged UnTracked files a.k.a UnTracked files (new files. Always unstaged. If staged, that means they are tracked)

1--removes Unstaged Tracked files ONLY [Type 2]
* git checkout .

2--removes Unstaged UnTracked files ONLY [Type 3]; There is no going back. Use -n or --dry-run to preview the damage you'll do.
* git clean -f  
* git clean -f -d (if you want to also remove subdirectories) 
* git clean -f -X (if you just want to remove ignored files)
* git clean -f -x (if you want to remove ignored as well as non-ignored files)

3--removes Staged Tracked and UnStaged Tracked files ONLY[Type 1, Type 2]
* git reset --hard 

4--removes all changes [Type 1, Type 2, Type 3]
* git stash -u 

##Conclusion:
We can use either:
1 combination of `git clean -f` and `git reset --hard` 
OR
2 `git stash –u`
### Note: Stashing, as the word means 'Store (something) safely and secretly in a specified place.' This can always be retrieved using git stash pop.

5--discarding all local commits on this branch [Removing local commits]
* git reset --hard origin/master [if local branch is master]

6--revert a commit already pushed to a remote repository
* git revert ab12cd15

## Delete a previous commit from local branch and remote branch:
1--deleting that commit from local branch
*git reset --hard HEAD~1

2--for deleting from remote branch, both the above and the following must be executed
* git push origin HEAD –force

## Remove local git merge:
Master branch merged with a newly working branch phase2:
* git status
* --On branch master
* git merge phase2
* git status
* --On branch master
* --Your branch is ahead of 'origin/master' by 8 commits.

1--to remove the merge
* git reset --hard origin/master
    OR
* git reset --hard HEAD~8
    OR 
* git reset --hard 9a88396f51e2a068bb7 [this is the one that was present before all your merge commits happened]

## Stashing Your Work 
<a href="https://git-scm.com/book/en/v2/Git-Tools-Stashing-and-Cleaning">More Details</a>

By default, git stash will only store files that are already in the index. If you specify --include-untracked or -u, Git will also stash any untracked files you have created.

1--Stash the changes
* git stash
* git stash -u  

2--To list the stashes
* git stash list

When having multiple stashes, you can reapply the one you just stashed by using the command shown in the help output of the original stash command: git stash apply. If you want to apply one of the older stashes, you can specify it by naming it, like this: 
* git stash apply stash@{2}

3--to tell the command to try to reapply the staged changes
* git stash apply --[filename]

4--to remove a stash
* git stash drop stash@{0}

5--to apply the stash and then immediately drop it from your stack
* git stash pop

6--to stash the files exept the filename file
* git stash --keep-(filename)

7--when you may not want to stash some work or files in your working directory, but simply get rid of them. 
* git clean  (reasons for this might be to remove cruft that has been generated by merges or external tools or to remove build artifacts in order to run a clean build)
* git stash --all (safer than the above command, because it removes everything and saves it in a stash)