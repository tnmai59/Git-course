```
C:\Users\HP\DSLab>git clone https://github.com/nnja/advanced-git-exercises.git
Cloning into 'advanced-git-exercises'...
remote: Enumerating objects: 28, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 28 (delta 0), reused 0 (delta 0), pack-reused 25  
Receiving objects: 100% (28/28), done.
Resolving deltas: 100% (1/1), done.

C:\Users\HP\DSLab>cd advanced-git-exercises

C:\Users\HP\DSLab\advanced-git-exercises>git checkout exercise2
Switched to a new branch 'exercise2'
branch 'exercise2' set up to track 'origin/exercise2'.
```

* Ex1: Use git ls-files -s to view the contents of the staging area.
```
C:\Users\HP\DSLab>git ls-files -s
100644 475935fb868586d53cd206a2cc525b1474bd15a7 0       hello.txt
```
*Ex2: Make a change and try to stage it interactively (git add -p).
```
C:\Users\HP\DSLab\advanced-git-exercises>echo "This is a test of the emergency git-casting system." >> hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git add -p
diff --git a/hello.txt b/hello.txt
index 980a0d5..b947a3d 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1 +1,2 @@
 Hello World!
+"This is a test of the emergency git-casting system." 
(1/1) Stage this hunk [y,n,q,a,d,e,?]? y
<stdin>:7: trailing whitespace.
"This is a test of the emergency git-casting system."
warning: 1 line adds whitespace errors.

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise2
Your branch is up to date with 'origin/exercise2'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git ls-files -s
100644 b947a3df8e546de4b69357e40b75ef0a4406b834 0       hello.txt
```
*Ex3:
```
C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise2
Your branch is up to date with 'origin/exercise2'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   hello.txt


C:\Users\HP\DSLab\advanced-git-exercises>git ls-files -s
100644 b947a3df8e546de4b69357e40b75ef0a4406b834 0       hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git reset hello.txt
Unstaged changes after reset:
M       hello.txt

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise2
Your branch is up to date with 'origin/exercise2'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)    
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
* Ex4:
```
C:\Users\HP\DSLab\advanced-git-exercises>git stash save "emergency git-casting"
Saved working directory and index state On exercise2: emergency 
git-casting

C:\Users\HP\DSLab\advanced-git-exercises>git status
On branch exercise2
Your branch is up to date with 'origin/exercise2'.

nothing to commit, working tree clean

C:\Users\HP\DSLab\advanced-git-exercises>git stash list
stash@{0}: On exercise2: emergency git-casting

C:\Users\HP\DSLab\advanced-git-exercises>git stash show stash@{0}
 hello.txt | 1 +
 1 file changed, 1 insertion(+)

C:\Users\HP\DSLab\advanced-git-exercises>git stash apply stash@{0}
On branch exercise2
Your branch is up to date with 'origin/exercise2'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)    
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")

C:\Users\HP\DSLab\advanced-git-exercises>git diff hello.txt
diff --git a/hello.txt b/hello.txt
index 980a0d5..b947a3d 100644
--- a/hello.txt
+++ b/hello.txt
@@ -1 +1,2 @@
 Hello World!
+"This is a test of the emergency git-casting system." 
```