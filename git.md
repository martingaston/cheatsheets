# Git Cheatsheet
### Or, when you've *really* gone and done it: https://blog.github.com/2015-06-08-how-to-undo-almost-anything-with-git/

### Pull a repo:

`$ git clone www_repo_url`

`$ git status`

### View Differences:

`$ git diff`

`$ git diff --cached`

`$ git diff HEAD`

`$ git diff commit1 commit2`

`$ git log`

### Switch Branch:

`$ git checkout -b my_branch`

`$ git branch`

`$ git branch -av`

`$ git checkout my_branch`

### Add to Staging & Commit:

`$ git add file`

`$ git add .`

`$ git commit -m 'update message'`

### Go Back in Time:

`$ git reset file`
`$ git reset --hard`

### Merge master into my_branch:

`$ git checkout master`

`$ git pull origin master`

`$ git checkout my_branch`

`$ git merge master`

### Push branch to GitHub

`$ git push origin my_branch`

### Switch between HTTPS or SSL

```bash
# check the current remote url
$ git remote -v
# change the url to SSH...
$ git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
# or change it to HTTPS...
$ git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
# verify it's changed :)
$ git remote -v 
```

### Create a repository on the command line

```bash
echo "# [REPONAME]" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:USERNAME/REPOSITORY.git #SSH
git push -u origin master # -u/--set-upstream sets an 'argument-less git pull' 
```