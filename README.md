# Git-course
While doing these exercises on Window 10, I took some notes and I hope it would be useful:
* `^` doesn't work on Window, Use `~<a number>` instead.
  For example, if you want to move the HEAD pointer back to the previous commit, but it will not remove the changes that were made in that commit from the working tree or the index, `git reset --soft HEAD~1` should be
  used instead of `git reset --soft HEAD^` as you saw in the solution.
* If want to display content of a file, use command `type <source><file name>` and need to convert all `/` to `\` in the source
* In ex8, use `git pull origin master --allow-unrelated-histories` instead of git `pull --rebase upstream master` (explaination here: https://www.educative.io/answers/the-fatal-refusing-to-merge-unrelated-histories-git-error)
* In ex10:
  - Command `cp ../../src/` doesn't work on Window. If you use window you need to subtitute that command with `copy ...\...\src`
  - Also in Ex10, I have problem when try to commit. The error is it cannot find my pre-commit file . Try to add the `#!/bin/sh` to your pre-commit file which **IN the folder hooks in .git folder**, else it wouldn't work as my case at first

