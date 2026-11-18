# Linux, Shell and Git Cheatsheet

## Navigation and files
- pwd: print the current directory
- ls -la: list all files with details
- cd <dir>, cd .., cd ~: move around
- mkdir -p a/b: create nested folders
- touch f: create an empty file
- cp src dst, mv src dst, rm f, rm -r dir: copy, move, delete

## Reading and searching
- cat, head -n 5, tail -n 5: read files
- grep "text" file: find matching lines (grep -c counts them)
- wc -l file: count lines
- cmd1 | cmd2: pipe, send the output of one command into the next

## Redirection
- > overwrites a file, >> appends to a file

## Permissions
- ls -l shows rwx for owner, group, others
- r = read, w = write, x = execute
- chmod +x script.sh makes a script executable

## Shell scripting
- Variables: NAME="Sidd", use as $NAME
- Command output in text: $(date)
- if [ -f file ]; then ... else ... fi
- for i in 1 2 3; do ... done

## Git
- git status, git add ., git commit -m "msg"
- git checkout -b branch: create and switch to a branch
- git merge branch: merge a branch into the current one
- git push, git log --oneline