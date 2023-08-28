```
C:\Users\HP\DSLab\advanced-git-exercises>git checkout exercise4
Switched to a new branch 'exercise4'
branch 'exercise4' set up to track 'origin/exercise4'.
```
1. Merge the exercise3 branch into exercise4, and look at the git log.
```
C:\Users\HP\DSLab\advanced-git-exercises>git merge exercise3
Updating 43388fe..e348ebc
Fast-forward
 hello.txt | 1 +
 1 file changed, 1 insertion(+)

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
e348ebc (HEAD -> exercise4, tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit
```
2. Use git reset --hard HEAD^ to reset your exercise4 branch back one commit, then use the --no-ff option to git merge to merge exercise3 again. Look at the git log, how is it different from the last step?
* git reset --hard HEAD^ not working on Window, I used git reset --soft HEAD~1 insted
```
C:\Users\HP\DSLab\advanced-git-exercises>git reset --soft HEAD~1

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
43388fe (HEAD -> exercise4, origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>git merge --no-ff exercise3
Merge made by the 'ort' strategy.

C:\Users\HP\DSLab\advanced-git-exercises>git log --graph
*   commit d63289627b098f25aa5e01ef5be2e64fa47ea456 (HEAD -> exercise4)
|\  Merge: 7c0c266 e348ebc
| | Author: tnmai59 <thieungocmai.watt@gmail.com>
| | Date:   Mon Aug 28 13:22:30 2023 +0700
| |
| |     Merge branch 'exercise3' into exercise4
| |
| * commit e348ebc1187cb3b4066b1e9432a614b464bf9d07 (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3)
| | Author: Nina Zakharenko <nina@nnja.io>
| | Date:   Wed Oct 4 19:01:12 2017 -0700
| |
| |     Testing the emergency git-casting system
| |
* | commit 7c0c26672e13f1230a8dea4f111a119fe4bc6d50
|/  Author: tnmai59 <thieungocmai.watt@gmail.com>
|   Date:   Mon Aug 28 13:22:24 2023 +0700
|
|       update hello.text
|
* commit 43388fee19744e8893467331d7853a6475a227b8 (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master)
  Author: Nina Zakharenko <nina@nnja.io>
  Date:   Wed Oct 4 18:51:49 2017 -0700

      Initial commit

```
3. Make two conflicting changes to hello.txt in two different branches.
```
C:\Users\HP\DSLab\advanced-git-exercises>git branch
  exercise2
  exercise3
* exercise4
  master

C:\Users\HP\DSLab\advanced-git-exercises>git checkout -b mundo
Switched to a new branch 'mundo'

C:\Users\HP\DSLab\advanced-git-exercises>git branch
  exercise2
  exercise3
  exercise4
  master
* mundo

C:\Users\HP\DSLab\advanced-git-exercises># Edit your hello.txt to say "Hello Mundo!"
'#' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\HP\DSLab\advanced-git-exercises>notepad hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch mundo
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")

C:\Users\HP\DSLab\advanced-git-exercises>git add hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Changing World to Mundo"
[mundo 8239907] Changing World to Mundo
 1 file changed, 1 insertion(+), 1 deletion(-)

C:\Users\HP\DSLab\advanced-git-exercises>git checkout exercise4
Switched to branch 'exercise4'
Your branch is ahead of 'origin/exercise4' by 3 commits.
  (use "git push" to publish your local commits)

C:\Users\HP\DSLab\advanced-git-exercises>notepad hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git add hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Changing world to Hola"
[exercise4 4775c60] Changing world to Hola
 1 file changed, 1 insertion(+), 1 deletion(-)
```
4. Enable ReReRe, then merge one branch into the other.
```
C:\Users\HP\DSLab\advanced-git-exercises>git config rerere.enabled true

C:\Users\HP\DSLab\advanced-git-exercises>git merge mundo
Auto-merging hello.txt
CONFLICT (content): Merge conflict in hello.txt
Recorded preimage for 'hello.txt'
Automatic merge failed; fix conflicts and then commit the result.

C:\Users\HP\DSLab\advanced-git-exercises>git rerere diff
--- a/hello.txt
+++ b/hello.txt
@@ -1,6 +1,6 @@
-<<<<<<<
+<<<<<<< HEAD
 Hello Hola!
-=======
+=======
 Hello Mundo!
->>>>>>>
+>>>>>>> mundo
 This is a test of the emergency git-casting system.

C:\Users\HP\DSLab\advanced-git-exercises>notpad hello.txt
'notpad' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\HP\DSLab\advanced-git-exercises>notepad hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git rerere diff   
--- a/hello.txt
+++ b/hello.txt
@@ -1,6 +1,6 @@
-<<<<<<<
+<<<<<<< HEAD
 Hello Hola!
-=======
-Hello Mundo!
->>>>>>>
+=======
+Hello Hola!
+>>>>>>> mundo
 This is a test of the emergency git-casting system.

C:\Users\HP\DSLab\advanced-git-exercises>git add hello.txt 

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Merging in mundo branch"
Recorded preimage for 'hello.txt'
[exercise4 139e190] Merging in mundo branch
```
5. Backup again with git reset --hard HEAD^, then attempt the merge again. Notice how ReReRe automatically resolves the conflict for you.
```
C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
139e190 (HEAD -> exercise4) Merging in mundo branch
4775c60 Changing world to Hola
8239907 (mundo) Changing World to Mundo
d632896 Merge branch 'exercise3' into exercise4
7c0c266 update hello.text
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>git reset --soft HEAD~1

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
4775c60 (HEAD -> exercise4) Changing world to Hola
d632896 Merge branch 'exercise3' into exercise4
7c0c266 update hello.text
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit
```