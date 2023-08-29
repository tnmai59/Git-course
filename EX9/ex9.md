* Ex1
```
C:\Users\HP\DSLab\advanced-git-exercises>git grep -e "Python"
python_code.py:# This is a Python file
python_code.py:    print("Welcome to Python!")

C:\Users\HP\DSLab\advanced-git-exercises> git grep --line-number --heading --break -e "Python"
python_code.py
1:# This is a Python file
4:    print("Welcome to Python!")

C:\Users\HP\DSLab\advanced-git-exercises> echo "More Python code" >> python_code.py

C:\Users\HP\DSLab\advanced-git-exercises>git grep --line-number -e "Python"             
python_code.py:1:# This is a Python file
python_code.py:4:    print("Welcome to Python!")
python_code.py:5:"More Python code"

C:\Users\HP\DSLab\advanced-git-exercises>git grep --line-number --cached -e "Python"
python_code.py:1:# This is a Python file
python_code.py:4:    print("Welcome to Python!")

C:\Users\HP\DSLab\advanced-git-exercises>git grep --line-number --cached -e "Python"
python_code.py:1:# This is a Python file
python_code.py:4:    print("Welcome to Python!")

C:\Users\HP\DSLab\advanced-git-exercises>git add python_code.py

C:\Users\HP\DSLab\advanced-git-exercises>git grep --line-number --cached -e "Python"
python_code.py:1:# This is a Python file
python_code.py:4:    print("Welcome to Python!")
python_code.py:5:"More Python code"
```
* Ex2:
```
C:\Users\HP\DSLab\advanced-git-exercises>git checkout python_code.py
Updated 0 paths from the index

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
88f6e28 (HEAD -> exercise9, upstream/exercise9) Adding bash, python, and java code examples
43388fe (upstream/master, upstream/exercise7, upstream/exercise4, upstream/exercise2, upstream/HEAD, origin/master, master) Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>git log exercise3 --oneline
e348ebc (tag: my-exercise3-tag, tag: exercise3-annotated-tag, upstream/exercise3, exercise3) Testing the emergency git-casting system
43388fe (upstream/master, upstream/exercise7, upstream/exercise4, upstream/exercise2, upstream/HEAD, origin/master, master) Initial commit

C:\Users\HP\DSLab\advanced-git-exercises>git cherry-pick e348ebc
error: your local changes would be overwritten by cherry-pick.
hint: commit your changes or stash them to proceed.
fatal: cherry-pick failed

C:\Users\HP\DSLab\advanced-git-exercises>git stash
Saved working directory and index state WIP on exercise9: 88f6e28 Adding bash, python, and java code examples

C:\Users\HP\DSLab\advanced-git-exercises>git cherry-pick e348ebc
[exercise9 67e9148] Testing the emergency git-casting system
 Author: Nina Zakharenko <nina@nnja.io>
 Date: Wed Oct 4 19:01:12 2017 -0700
 1 file changed, 1 insertion(+)

C:\Users\HP\DSLab\advanced-git-exercises>git log --oneline
67e9148 (HEAD -> exercise9) Testing the emergency git-casting system
88f6e28 (upstream/exercise9) Adding bash, python, and java code examples
43388fe (upstream/master, upstream/exercise7, upstream/exercise4, upstream/exercise2, upstream/HEAD, origin/master, master) Initial commit
```
*Ex3:
```
C:\Users\HP\DSLab\advanced-git-exercises>git blame hello.txt
^43388fe (Nina Zakharenko 2017-10-04 18:51:49 -0700 1) Hello World!
67e9148f (Nina Zakharenko 2017-10-04 19:01:12 -0700 2) This is a test of the emergency git-casting system.

C:\Users\HP\DSLab\advanced-git-exercises>git rm java_code.java
rm 'java_code.java'

C:\Users\HP\DSLab\advanced-git-exercises>git commit -m "Who uses Java anyway?"
[exercise9 800c8c9] Who uses Java anyway?
 1 file changed, 7 deletions(-)
 delete mode 100644 java_code.java

C:\Users\HP\DSLab\advanced-git-exercises>git log --diff-filter=D -- java_code.java
commit 800c8c95cea9d5347db970b2b67c926cbf029ac2 (HEAD -> exercise9)
Author: tnmai59 <thieungocmai.watt@gmail.com>
Date:   Tue Aug 29 18:19:01 2023 +0700

    Who uses Java anyway?

C:\Users\HP\DSLab\advanced-git-exercises>git blame 800c8c95cea9d5347db970b2b67c926cbf029ac2~1 -- java_code.java
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 1) // This is a Java file
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 2)
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 3) public class HelloWorld {        
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 4)    public static void main(String[] args) {
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 5)       System.out.println("Привет 
от Java!");
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 6)    }
88f6e286 (Nina Zakharenko 2017-10-05 11:31:34 -0700 7) }
```
* Ex3:
```
C:\Users\HP\DSLab\advanced-git-exercises>git bisect start 800c8c9 43388fe
Already on 'exercise9'
Your branch is ahead of 'upstream/exercise9' by 2 commits.
  (use "git push" to publish your local commits)
Bisecting: 0 revisions left to test after this (roughly 1 step)
[67e9148f82c1bbdfbcd91e6a1b9b34b849945242] Testing the emergency git-casting system

C:\Users\HP\DSLab\advanced-git-exercises>type hello.txt
Hello World!
This is a test of the emergency git-casting system.

C:\Users\HP\DSLab\advanced-git-exercises>git bisect bad
Bisecting: 0 revisions left to test after this (roughly 0 steps)
[88f6e2864bd0829c71654f1d19096f436a66ce07] Adding bash, python, and java code examples

C:\Users\HP\DSLab\advanced-git-exercises>type hello.txt
Hello World!

C:\Users\HP\DSLab\advanced-git-exercises>git bisect good
67e9148f82c1bbdfbcd91e6a1b9b34b849945242 is the first bad commit
commit 67e9148f82c1bbdfbcd91e6a1b9b34b849945242
Author: Nina Zakharenko <nina@nnja.io>
Date:   Wed Oct 4 19:01:12 2017 -0700

    Testing the emergency git-casting system

 hello.txt | 1 +
 1 file changed, 1 insertion(+)

```