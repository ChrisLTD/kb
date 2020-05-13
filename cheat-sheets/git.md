# Git

### Commands

Remove a file from the repo without deleting it:`git rm --cached MYFILE.TXT`

Remove a directory from the repo without deleting it:`git rm --cached -r MYDIRECTORY`

### Aliases to add to .gitconfig file

```text
[alias]
  co = checkout
  ec = config --global -e
  up = !git pull --rebase --prune $@ && git submodule update --init --recursive
  cob = checkout -b
  cm = !git add -A && git commit -m
  save = !git add -A && git commit -m 'SAVEPOINT'
  wip = !git add -u && git commit -m "WIP"
  undo = reset HEAD~1 --mixed
  amend = commit -a --amend
  wipe = !git add -A && git commit -qm 'WIPE SAVEPOINT' && git reset HEAD~1 --hard
  bclean = "!f() { git branch --merged ${1-master} | grep -v " ${1-master}$" | xargs -r g:it branch -d; }; f"
  bdone = "!f() { git checkout ${1-master} && git up && git bclean ${1-master}; }; f"
  st = status
  logp = log --pretty=oneline --max-count=20
  subinit = !git submodule init && git submodule update
```

