1. Make bad changes to a file, then use git checkout to fix it. Use git checkout to reset your file back to an earlier point in time.
```
C:\Users\HP\DSLab\advanced-git-exercises>echo "bad change" > hello.template

C:\Users\HP\DSLab\advanced-git-exercises>type hello.template
"bad change" 

C:\Users\HP\DSLab\advanced-git-exercises>git checkout -- hello.template

C:\Users\HP\DSLab\advanced-git-exercises>type hello.template
[greeting] [noun]!
This is a test of the emergency git-casting system.

C:\Users\HP\DSLab\advanced-git-exercises>git log --name-status --follow --oneline hello.template
4b2b90e (HEAD -> exercise6, origin/exercise6) Replacing greeting with tokens for i18n
R073    hello.txt       hello.template
fec9e7b Changing Hello to Hola
M       hello.txt
afa34a6 Changing World to Mundo
M       hello.txt
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
M       hello.txt
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit
A       hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git checkout fec9e7b -- hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>type hello.txt
Hola World!
This is a test of the emergency git-casting system.

C:\Users\HP\DSLab\advanced-git-exercises>git reset HEAD hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git rm hello.template
rm 'hello.template'

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise6
Your branch is up to date with 'origin/exercise6'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    hello.template

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.txt


C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Deleting hello.template"
[exercise6 47f11b3] Deleting hello.template
 1 file changed, 2 deletions(-)
 delete mode 100644 hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git log --diff-filter=D --oneline -- hello.template
47f11b3 (HEAD -> exercise6) Deleting hello.template


C:\Users\HP\DSLab\advanced-git-exercises>git checkout 47f11b3~1 -- hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   hello.template

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.txt
```
2. Use git clean to remove untracked files from your repo. Remember to use --dry-run first.
```
C:\Users\HP\DSLab\advanced-git-exercises>git clean --dry-run
Would remove hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git clean -f
Removing hello.txt
```
3. Stage a change and then use git reset to unstage it. Use git reset --hard to reset your branch back pointer, staging area, and working area to an earlier commit. Use "mixed mode" to reset your branch back to an earlier commit, then use ORIG_HEAD to reset your branch back to where you were.
```
C:\Users\HP\DSLab\advanced-git-exercises>git reset

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git rm -f hello.template
rm 'hello.template'

C:\Users\HP\DSLab\advanced-git-exercises>cat hello.template
'cat' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\HP\DSLab\advanced-git-exercises>type hello.template
The system cannot find the file specified.

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
47f11b3 (HEAD -> exercise6) Deleting hello.template
4b2b90e (origin/exercise6) Replacing greeting with tokens for i18n
ff91b70 (origin/exercise5) Merging in mundo branch
fec9e7b Changing Hello to Hola
4582f72 Merge branch 'exercise3' into exercise4
afa34a6 Changing World to Mundo
7ea8b01 Merge branch 'exercise3' into exercise4
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>git reset 4b2b90e -- hello.template
Unstaged changes after reset:
D       hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   hello.template

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    hello.template


C:\Users\HP\DSLab\advanced-git-exercises>type hello.template
The system cannot find the file specified.
```
```
C:\Users\HP\DSLab\advanced-git-exercises>git reset --hard HEAD
HEAD is now at 47f11b3 Deleting hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git log -2 --oneline
47f11b3 (HEAD -> exercise6) Deleting hello.template
4b2b90e (origin/exercise6) Replacing greeting with tokens for i18n

C:\Users\HP\DSLab\advanced-git-exercises>git reset 4b2b90e 
Unstaged changes after reset:
D       hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git log -1 --oneline
4b2b90e (HEAD -> exercise6, origin/exercise6) Replacing greeting with tokens for i18n

C:\Users\HP\DSLab\advanced-git-exercises>git reset ORIG_HEAD

C:\Users\HP\DSLab\advanced-git-exercises>git log -1 --oneline
47f11b3 (HEAD -> exercise6) Deleting hello.template
```
4. Practice using git revert to safely revert a commit with a new commit.
```
C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise6
Revert "Deleting hello.template"

This reverts commit 47f11b3a83736b515a0085bbfdca9f8af674d4c3.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch exercise6
# Your branch is ahead of 'origin/exercise6' by 1 commit.
#   (use "git push" to publish your local commits)
#
# Changes to be committed:
#       new file:   hello.template
#
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise6
Your branch is ahead of 'origin/exercise6' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   hello.template

C:\Users\HP\DSLab\advanced-git-exercises>type hello.template
[greeting] [noun]!
This is a test of the emergency git-casting system.
```
