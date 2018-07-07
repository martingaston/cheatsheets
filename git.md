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