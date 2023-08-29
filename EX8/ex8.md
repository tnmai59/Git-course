
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



```