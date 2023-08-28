```
C:\Users\HP\DSLab\advanced-git-exercises>git checkout exercise3
Switched to a new branch 'exercise3'
branch 'exercise3' set up to track 'origin/exercise3'.
```
*Ex1 : Check the value of your HEAD variable (hint: look in .git) and confirm you're pointed at the exercise3 branch.
```
C:\Users\HP\DSLab\advanced-git-exercises>type .git\HEAD
ref: refs/heads/exercise3

C:\Users\HP\DSLab\advanced-git-exercises>git branch
  exercise2
* exercise3
  master
```
* Ex2: Use show-ref to look at your other heads.
```
C:\Users\HP\DSLab\advanced-git-exercises>git show-ref --heads
70bddcbfd1ceb5dd7d493e1a0a749f0a07200ccc refs/heads/exercise2
e348ebc1187cb3b4066b1e9432a614b464bf9d07 refs/heads/exercise3
43388fee19744e8893467331d7853a6475a227b8 refs/heads/master
```
* Ex3: Create a lightweight tag and confirm that it's pointing at the right commit.
```
C:\Users\HP\DSLab\advanced-git-exercises>git cat-file -p 43388fee19744e8893467331d7853a6475a227b8
tree 581caa0fe56cf01dc028cc0b089d364993e046b6
author Nina Zakharenko <nina@nnja.io> 1507168309 -0700
committer Nina Zakharenko <nina@nnja.io> 1507168309 -0700

Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>git cat-file -p e348ebc1187cb3b4066b1e9432a614b464bf9d07
tree cbcdf5dda7853d595fe0b1942cb0d1d72eb910f3
parent 43388fee19744e8893467331d7853a6475a227b8
author Nina Zakharenko <nina@nnja.io> 1507168872 -0700
committer Nina Zakharenko <nina@nnja.io> 1507168872 -0700

Testing the emergency git-casting system

C:\Users\HP\DSLab\advanced-git-exercises>git tag my-exercise3-tag

C:\Users\HP\DSLab\advanced-git-exercises>git show-ref --tags
e348ebc1187cb3b4066b1e9432a614b464bf9d07 refs/tags/my-exercise3-tag

C:\Users\HP\DSLab\advanced-git-exercises>git tag --points-at e348ebc
my-exercise3-tag
```
* Ex4: Create an annotated tag, and use git show to see more information about it.
```
C:\Users\HP\DSLab\advanced-git-exercises>git tag -a "exercise3-annotated-tag" -m "This is my annotated tag for exercise 3"

C:\Users\HP\DSLab\advanced-git-exercises>git show exercise3-annotated-tag
tag exercise3-annotated-tag
Tagger: tnmai59 <thieungocmai.watt@gmail.com>
Date:   Mon Aug 28 12:56:03 2023 +0700

This is my annotated tag for exercise 3

commit e348ebc1187cb3b4066b1e9432a614b464bf9d07 (HEAD -> exercise3, tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3)
Author: Nina Zakharenko <nina@nnja.io>
Date:   Wed Oct 4 19:01:12 2017 -0700

    Testing the emergency git-casting system

diff --git a/hello.txt b/hello.txt
index 980a0d5..b31a35b 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1 +1,2 @@
 Hello World!
+This is a test of the emergency git-casting system.
```
*Ex5: Get into a "detached HEAD" state by checking out a specific commit, then confirm that your HEAD is pointing at this commit rather than at a branch.
```
e348ebc (HEAD -> exercise3, tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>git checkout e348ebc
Note: switching to 'e348ebc'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at e348ebc Testing the emergency git-casting system

C:\Users\HP\DSLab\advanced-git-exercises>type .git\HEAD
e348ebc1187cb3b4066b1e9432a614b464bf9d07
```
* Ex6: Make a new commit, then switch branches to confirm that you're leaving a commit behind.
```
C:\Users\HP\DSLab\advanced-git-exercises>echo "This is a test file" > dangle.txt

C:\Users\HP\DSLab\advanced-git-exercises>git add dangle.txt

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "This is a dangling commit"
[detached HEAD ba2275b] This is a dangling commit
 1 file changed, 1 insertion(+)
 create mode 100644 dangle.txt

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
ba2275b (HEAD) This is a dangling commit
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, origin/exercise3, exercise3) Testing the emergency git-casting system
43388fe (origin/master, origin/exercise7, origin/exercise4, origin/exercise2, origin/HEAD, master) Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>type .git\HEAD
ba2275b902d61be9c554f73c113100e43b650edd

```