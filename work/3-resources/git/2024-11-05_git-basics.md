---
aliases:
  - git-basics
  - A simple collection of commands foundamental to git
tags: []
title: git-basics
---

# A simple collection of commands foundamental to git

Add files to stagging area
- git add . adds everthing from the current directory recursively

See git config
- git config --global --list 

Commit messages
- git commit -m "<message>", commits the staged changed with the inserted commit message
- git commit, opens the default editor to write the full commit message

Remove staged files from index
- git rm --cached <file-name>, removes the file from the stagging area and removes itfrom index. It's no longer tracked.
- git reset <file-name>, removes file from stagging area but not the index.

Delete file
- git rm <file-name>, remove from staggings area. In the commit the file appears as being deleted. Deletes from working dir.

Get a previous version
- git checkout <file-name>, discard changes made to this specific file in the working dir, reverts to last commit state. All changes made are lost. 
- git checkout ., resets all modified files.
- git checkout <hash-commit> -- <filne-name>

Reset HEAD pointer; two modes
- git reset --soft HEAD~1, moves the HEAD pointer back 1 commit. Keep changes staged. Does not affect working dir.
- git reset --hard HEAD~1, moves the HEAD pointer back 1 commit. Clears the stagging area. Fully resets the working dir to the state of last commit. All the changes are lost.

Commit information/history
- git log, give all the available info about all the commit history
- git log --oneline, only displays commit hash and message.
- git show, displays all available information about last commit.
- git log -p, makes it even more verbose displying diff info. Let's break down and exemple:
```bash
commit 4eaa7b65ffc8b2977604ef05b2d5b00762e16551
Author: John Doe <student@example.com>
Date:   Wed Nov 6 16:04:06 2024 +0000

    another work on master

diff --git a/testfile-04 b/testfile-04
index 02f7874..51162bf 100644
--- a/testfile-04
+++ b/testfile-04
@@ -1 +1,2 @@
 fourth file
+another work
```
The diff block 'diff --git a/testfile-04 b/testfile-04' tells that the changes are for this file. a/testfile-04 is the old version and b/testfile-04 is the new version.
'index 02f7874..51162bf 100644' displays the commit hash of the files. 
@@ -<old-line-number>,<num-lines> +<new-line-number>,<num-lines> @@ indicates that the changes start in <old-line-number>, and go for <num-lines>. <new-line-number> the line number in the new file the change starts, <num-lines> tells the number of lines in the new file that are involved in thechange. 'fourth file' was keeped and 'another work' was added.

Querying commits
- git log --author="John Doe", search commits of this author. Can also use regex.
- can also use grep. For instance consider a commit with JIRA-1234, then one can simply, git log --grep='JIRA-1234'
- git log -- <file-name>, (the space -- ensure git treats the <file-name> as a file name) searchs for commits involving this file.
  - git log -- <file-name1> <file-name2>, same thing but for mutiple files

Compare branches
- git log <branch1>..<branch2>, used to show the commits in <branch2> that are not in <branch1> 


git tags
git tag -a v1.0 -m "version 1.0. initial state"

Merging branches
- git branch, lists all available branches. 
- git checkout -b  <branch-name>, creates a new branch a moves the head there.
- git branch -r, lists all branchs available in remote. 
    - origin/main
    - origin/feature-branch
    - upstream/main
    - upstream/feature-branch
- git merge <branch-name>, merges currenct active branch with <branch-name>.


Merge conflicts
On branch 1 there is the following:
Hello, world!
This is my change in the main branch.

On branch 2 there is the following:
Hello, world!
This is my change in the feature-branch.
By merging line 2 has a conflict. It is displayed in the following way,
```stdout
Hello, world!
<<<<<<< HEAD
This is my change in the main branch.
=======
This is my change in the feature-branch.
>>>>>>> feature-branch
```
Is up to the you to choose what to keep. This marks are present in the file where the conflict occurs. 

As a general note, it's good practice to merge master into branch and then do the reverse.


Git rebase
This is a good tutorial on the command list needed to performe a rebase [tutorial](https://www.themoderncoder.com/a-better-git-workflow-with-rebase/)










