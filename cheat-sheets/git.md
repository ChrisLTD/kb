# Git

### Commands

Remove a file from the repo without deleting it:`git rm --cached MYFILE.TXT`

Remove a directory from the repo without deleting it:`git rm --cached -r MYDIRECTORY`

Search through git branches: `git branch --all | grep -i MYSEARCH`

#### Reset remote "busted\_branch" with the contents of a "better\_branch"

Make sure everything is pushed up to your remote repository, then checkout your `busted_branch`:

```
git checkout busted_branch
```

Overwrite `busted_branch` with `better_branch`:

```
git reset --hard better_branch
```

Force the push to your remote:

```
git push -f origin busted_branch
```

Resolve conflicted file with "their" changes:

```
git checkout --theirs path/to/file
```

Resolve conflicted file with "our" changes:

```
git checkout --ours path/to/file
```

### Aliases to add to .gitconfig file

To prevent weird indenting, set paste mode in vim: `:set paste`

```
[user]
  name = Your Name
  email = your@email.com
[core]
  quotepath = false
  autocrlf = input
  editor = 'vim'
[push]
  default = simple
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

When done pasting: `:set nopaste`
