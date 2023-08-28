```
C:\Users\HP\DSLab\advanced-git-exercises>git checkout exercise5
Switched to a new branch 'exercise5'
branch 'exercise5' set up to track 'origin/exercise5'.
```
1. Practice creating a well-crafted commit - look at the format given on the slides for help.
```
C:\Users\HP\DSLab\advanced-git-exercises>notepad hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>type hello.txt
[greeting] [noun]!
This is a test of the emergency git-casting system.
C:\Users\HP\DSLab\advanced-git-exercises>git mv hello.txt hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git add hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Rename hello.txt to hello.template"
[exercise5 e775f22] Rename hello.txt to hello.template
 1 file changed, 1 insertion(+), 1 deletion(-)
 rename hello.txt => hello.template (73%)
```
2. Use git log to find commits created since yesterday. Rename a file and use the --name-status and --follow options to git log to track down when the file was renamed, and what it used to be called. Use --grep to search within commit messages, and --diff-filter to find renamed and modified files from git log.
```
C:\Users\HP\DSLab\advanced-git-exercises>git log --since="yesterday"
commit e775f22c336b9cc1ec649ef31439ff3210de8734 (HEAD -> exercise5)
Author: tnmai59 <thieungocmai.watt@gmail.com>
Date:   Mon Aug 28 14:09:27 2023 +0700

    Rename hello.txt to hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git log --name-status --follow --oneline hello.template
e775f22 (HEAD -> exercise5) Rename hello.txt to hello.template
R073    hello.txt       hello.template
fec9e7b Changing Hello to Hola
M       hello.txt
afa34a6 Changing World to Mundo
M       hello.txt
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
M       hello.txt
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit
A       hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git log --diff-filter=R --find-renames
commit e775f22c336b9cc1ec649ef31439ff3210de8734 (HEAD -> exercise5)
Author: tnmai59 <thieungocmai.watt@gmail.com>
Date:   Mon Aug 28 14:09:27 2023 +0700

    Rename hello.txt to hello.template

C:\Users\HP\DSLab\advanced-git-exercises>git log --diff-filter=M --oneline
fec9e7b Changing Hello to Hola
afa34a6 Changing World to Mundo
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
```
3. Use git show to get more information about a specific git hash.
```
C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
e775f22 (HEAD -> exercise5) Rename hello.txt to hello.template
ff91b70 (origin/exercise5) Merging in mundo branch
fec9e7b Changing Hello to Hola
4582f72 Merge branch 'exercise3' into exercise4
afa34a6 Changing World to Mundo
7ea8b01 Merge branch 'exercise3' into exercise4
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>git show ff91b70
commit ff91b70c7f23de6b168dc60478f270e8e3f992a8 (origin/exercise5)
Merge: fec9e7b afa34a6
Author: Nina Zakharenko <nina@nnja.io>
Date:   Wed Oct 4 19:51:40 2017 -0700

    Merging in mundo branch

diff --cc hello.txt
index 72e64a7,3dc2209..7018e35
--- a/hello.txt
+++ b/hello.txt
@@@ -1,2 -1,2 +1,2 @@@
- Hola World!
 -Hello Mundo!
++Hola Mundo!
  This is a test of the emergency git-casting system.
```
4. Try the --merged and --no-merged options to git branch to see which branches have been merged into master (or not).
```
C:\Users\HP\DSLab\advanced-git-exercises>git branch --merged master
  master

C:\Users\HP\DSLab\advanced-git-exercises>git branch --no-merged master
  exercise2
  exercise3
  exercise4
* exercise5
  mundo
```