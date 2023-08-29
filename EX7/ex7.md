1. Make a commit, then practice using the --amend option to make another change to the previous commit.
```
- After commit first.txt, i forgot to commit second.txt
C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise7
Your branch is ahead of 'origin/exercise7' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   second.txt

- Now I want to use git commit --amend --no-edit to change my prev commit
C:\Users\HP\DSLab\advanced-git-exercises>git commit --amend --no-edit
[exercise7 772a930] Committing two new files
 Date: Mon Aug 28 15:49:04 2023 +0700       
 3 files changed, 4 insertions(+)
 create mode 100644 first.txt
 create mode 100644 hello.template
 create mode 100644 second.txt

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise7
Your branch is ahead of 'origin/exercise7' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

```
2. Make two non-conflicting changes to two different branches. Rebase one branch onto the other.
```
- Set up for rebase
C:\Users\HP\DSLab\advanced-git-exercises>git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

C:\Users\HP\DSLab\advanced-git-exercises>git checkout -b exercise7-2
Switched to a new branch 'exercise7-2'

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
43388fe (HEAD -> exercise7-2, origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit
```
```
Add new feature and commit to branch exercise7-2
C:\Users\HP\DSLab\advanced-git-exercises>echo "New feature" > feature.txt

C:\Users\HP\DSLab\advanced-git-exercises>git add feature.txt

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Adding a new feature"
[exercise7-2 7f874a0] Adding a new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt

C:\Users\HP\DSLab\advanced-git-exercises>git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

C:\Users\HP\DSLab\advanced-git-exercises>echo "Master has continued to change" >> hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git add hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Master has continued to change"
[master 0a0d76f] Master has continued to change
 1 file changed, 1 insertion(+)

C:\Users\HP\DSLab\advanced-git-exercises>git checkout exercise7-2
Switched to branch 'exercise7-2'

C:\Users\HP\DSLab\advanced-git-exercises>git rebase master
Successfully rebased and updated refs/heads/exercise7-2.

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
6f929a4 (HEAD -> exercise7-2) Adding a new feature
0a0d76f (master) Master has continued to change
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD) Initial commit
```
3. Make another change to your current branch. Use an interactive rebase (git rebase -i) to rebase the two branches. Try squashing your two commits and rewording the message during the rebase.
```
C:\Users\HP\DSLab\advanced-git-exercises>echo "Another new feature" > another_feature.txt

C:\Users\HP\DSLab\advanced-git-exercises>git add another_feature.txt

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Adding another new feature"
[exercise7-2 22b1259] Adding another new feature
 1 file changed, 1 insertion(+)
 create mode 100644 another_feature.txt

C:\Users\HP\DSLab\advanced-git-exercises>git log -n 3 --oneline
22b1259 (HEAD -> exercise7-2) Adding another new feature
6f929a4 Adding a new feature
0a0d76f (master) Master has continued to change

C:\Users\HP\DSLab\advanced-git-exercises>git rebase -i HEAD~1
error: invalid command 'rpick'
error: invalid line 1: rpick 22b1259 Adding another new feature
You can fix this with 'git rebase --edit-todo' and then run 'git rebase --continue'.    
Or you can abort the rebase with 'git rebase --abort'.

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
6f929a4 (HEAD) Adding a new feature
0a0d76f (master) Master has continued to change
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD) Initial commit
```