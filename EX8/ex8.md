
```
C:\Users\HP\DSLab\advanced-git-exercises> git remote -v
origin  https://github.com/nnja/advanced-git-exercises.git (fetch)
origin  https://github.com/nnja/advanced-git-exercises.git (push)

C:\Users\HP\DSLab\advanced-git-exercises>git remote rename origin upstream
Renaming remote references: 100% (11/11), done.

C:\Users\HP\DSLab\advanced-git-exercises>git remote add origin https://github.com/tnmai59/advanced-git-exercises.git

C:\Users\HP\DSLab\advanced-git-exercises> git remote -v
origin  https://github.com/tnmai59/advanced-git-exercises.git (fetch)
origin  https://github.com/tnmai59/advanced-git-exercises.git (push)
upstream        https://github.com/nnja/advanced-git-exercises.git (fetch)
upstream        https://github.com/nnja/advanced-git-exercises.git (push)

C:\Users\HP\DSLab\advanced-git-exercises>git checkout master
Already on 'master'
Your branch is ahead of 'upstream/master' by 1 commit.
  (use "git push" to publish your local commits)

C:\Users\HP\DSLab\advanced-git-exercises>git pull origin master --allow-unrelated-histories
From https://github.com/tnmai59/advanced-git-exercises
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master
Already up to date.

C:\Users\HP\DSLab\advanced-git-exercises>git branch --set-upstream-to origin/master     
branch 'master' set up to track 'origin/master'.

C:\Users\HP\DSLab\advanced-git-exercises>echo "Change to upstream" > upstream_change.txt

C:\Users\HP\DSLab\advanced-git-exercises>git add upstream_change.txt

C:\Users\HP\DSLab\advanced-git-exercises>git checkout -b feature 
Switched to a new branch 'feature'

C:\Users\HP\DSLab\advanced-git-exercises>echo "change to local repo" > local_change.txt

C:\Users\HP\DSLab\advanced-git-exercises>git add .

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Change to local repo"
[feature 0fc96e1] Change to local repo
 1 file changed, 1 insertion(+)
 create mode 100644 local_change.txt

C:\Users\HP\DSLab\advanced-git-exercises>git pull --rebase upstream master
From https://github.com/nnja/advanced-git-exercises
 * branch            master     -> FETCH_HEAD
fatal: It seems that there is already a rebase-merge directory, and
I wonder if you are in the middle of another rebase.  If that is the
case, please try
        git rebase (--continue | --abort | --skip)
If that is not the case, please
        rm -fr ".git/rebase-merge"
and run me again.  I am stopping in case you still have something
valuable there.


C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
0fc96e1 (HEAD -> feature) Change to local repo
43388fe (upstream/master, upstream/exercise7, upstream/exercise4, upstream/exercise2, upstream/HEAD, origin/master, master) Initial commit

```