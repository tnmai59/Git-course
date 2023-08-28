* Ex1
```
C:\Users\HP>cd DSLab

C:\Users\HP\DSLab>git status
warning: could not open directory 'Application Data/': Permission denied
warning: could not open directory 'Cookies/': Permission denied 
warning: could not open directory 'Local Settings/': Permission 
denied
warning: could not open directory 'My Documents/': Permission denied
warning: could not open directory 'NetHood/': Permission denied 
warning: could not open directory 'PrintHood/': Permission denied
warning: could not open directory 'Recent/': Permission denied  
warning: could not open directory 'SendTo/': Permission denied  
warning: could not open directory 'Start Menu/': Permission denied
warning: could not open directory 'Templates/': Permission denied
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)        ../.bash_history
        ../.conda/
        ../.gitconfig
        ../.ipython/
        ../.jupyter/
        ../.lesshst
        ../.matplotlib/
        ../.vscode/
        ../AppData/
        ../Book/
        ../DSA/
        ../Desktop/
        ../Documents/
        ../Downloads/
        ../Git-course/
        "../Homework 7 _Thi\341\273\201u Ng\341\273\215c Mai_11213717.ipynb"
        ../IntelGraphicsProfiles/
        ../Links/
        ../ML/
        ../Microsoft/
        ../MicrosoftEdgeBackups/
        ../Music/
        ../NTUSER.DAT
        ../NTUSER.DAT{d2c93181-8e4b-11eb-8193-c30994652682}.TM.blf
        ../NTUSER.DAT{d2c93181-8e4b-11eb-8193-c30994652682}.TMContainer00000000000000000001.regtrans-ms
        ../NTUSER.DAT{d2c93181-8e4b-11eb-8193-c30994652682}.TMContainer00000000000000000002.regtrans-ms
        ../OneDrive - National Economics University/
        ../OneDrive/
        ../Pictures/
        ../PycharmProjects/
        ../Python/
        ../RStudio/
        ../Searches/
        ../Untitled Folder 1/
        ../Videos/
        ../anaconda3/
        ../dseb-64b/
        ../ntuser.dat.LOG1
        ../ntuser.dat.LOG2
        ../ntuser.ini
        ../py-homework/

nothing added to commit but untracked files present (use "git add" to track)

C:\Users\HP\DSLab>git init
Initialized empty Git repository in C:/Users/HP/DSLab/.git/
```
* Ex2:
```
C:\Users\HP\DSLab>echo "Hello world" > hello.txt

C:\Users\HP\DSLab>git add hello.txt

C:\Users\HP\DSLab>git commit -m "initial commit"
[master (root-commit) e064ea1] initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 hello.txt
```
* Ex3:
```
C:\Users\HP\DSLab>tree .git /A /F
Folder PATH listing for volume Windows
Volume serial number is 0000007A 64F5:9D3F
C:\USERS\HP\DSLAB\.GIT
|   COMMIT_EDITMSG
|   config
|   description
|   HEAD
|   index
|
+---hooks
|       applypatch-msg.sample
|       commit-msg.sample
|       fsmonitor-watchman.sample
|       post-update.sample
|       pre-applypatch.sample
|       pre-commit.sample
|       pre-merge-commit.sample
|       pre-push.sample
|       pre-rebase.sample
|       pre-receive.sample
|       prepare-commit-msg.sample
|       push-to-checkout.sample
|       sendemail-validate.sample
|       update.sample
|
+---info
|       exclude
|
+---logs
|   |   HEAD
|   |
|   \---refs
|       \---heads
|               master
|
+---objects
|   +---47
|   |       5935fb868586d53cd206a2cc525b1474bd15a7
|   |
|   +---d1
|   |       d28a987708eababd105df40fd584e4f6caf403
|   |       
|   +---e0
|   |       64ea145d3acf1de26ccb1a24d7fd07f8766f0d
|   |
|   +---info
|   \---pack
\---refs
    +---heads
    |       master
    |
    \---tags
```
*Ex4:
```
C:\Users\HP\DSLab>git cat-file -t 475935
blob

C:\Users\HP\DSLab>git cat-file -p 475935
"Hello world" 

C:\Users\HP\DSLab>git cat-file -t d1d28
tree

C:\Users\HP\DSLab>git cat-file -p d1d28
100644 blob 475935fb868586d53cd206a2cc525b1474bd15a7    hello.txt

C:\Users\HP\DSLab>git cat-file -t e064ea
commit

C:\Users\HP\DSLab>git cat-file -p e064ea
tree d1d28a987708eababd105df40fd584e4f6caf403
author tnmai59 <thieungocmai.watt@gmail.com> 1693196586 +0700   
committer tnmai59 <thieungocmai.watt@gmail.com> 1693196586 +0700
initial commit
```

*Ex 5
```
C:\Users\HP\DSLab>type .git\HEAD
ref: refs/heads/master

C:\Users\HP\DSLab>type .git\refs\heads\master 
e064ea145d3acf1de26ccb1a24d7fd07f8766f0d

C:\Users\HP\DSLab>git log --oneline
e064ea1 (HEAD -> master) initial commit

C:\Users\HP\DSLab>git branch new_branch

C:\Users\HP\DSLab>tree .git /A /F
Folder PATH listing for volume Windows
Volume serial number is 0000008C 64F5:9D3F
C:\USERS\HP\DSLAB\.GIT
|   COMMIT_EDITMSG
|   config
|   description
|   HEAD
|   index
|
+---hooks
|       applypatch-msg.sample
|       commit-msg.sample
|       fsmonitor-watchman.sample
|       post-update.sample
|       pre-applypatch.sample
|       pre-commit.sample
|       pre-merge-commit.sample
|       pre-push.sample
|       pre-rebase.sample
|       pre-receive.sample
|       prepare-commit-msg.sample
|       push-to-checkout.sample
|       sendemail-validate.sample
|       update.sample
|
+---info
|       exclude
|
+---logs
|   |   HEAD
|   |   
|   \---refs
|       \---heads
|               master
|               new_branch
|
+---objects
|   +---47
|   |       5935fb868586d53cd206a2cc525b1474bd15a7
|   |
|   +---d1
|   |       d28a987708eababd105df40fd584e4f6caf403
|   |
|   +---e0
|   |       64ea145d3acf1de26ccb1a24d7fd07f8766f0d
|   |
|   +---info
|   \---pack
\---refs
    +---heads
    |       master
    |       new_branch
    |
    \---tags

```