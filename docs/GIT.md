# Git Cheatsheet

## Cloning our core (github) repos

```sh
# CMS
git clone git@github.com:brooksidestudios/cms.git

# Blog (from root folder)
git clone git@github.com:brooksidestudios/blog.git app/Plugin/Blog

# Gallery (from root folder)
git clone git@github.com:brooksidestudios/gallery.git app/Plugin/Gallery

# Store
git clone git@github.com:brooksidestudios/store.git
```

## Cloning our repos from Bitbucket

```sh
git clone git@bitbucket.com:brooksidestudios/repo-name.git
```

## Stage files to be committed to the repo

```sh
# All files and folders
git add -A

# A specific file or folder
git add app/webroot/favicon.ico
```

## Committing and pushing

```sh
# Make a commit with a message of "Fix bug"
git commit -m "Fix bug"

# Pushing the changes back out to its remote repository
git push origin master

# Or, simply
git push
```

## Other useful commands

```sh
# Display the current status – modified files, files staged, files not yet staged, etc.
git status

# List previous commits
git log

# Checkout a previous commit
git checkout [commit id]

# Switch to a branch (this will create a new branch if it doesn't exist)
git checkout -b branch-name

# Delete a branch
git branch -d branch-name

# Switch back to master (checkout master)
git checkout master

# Merge branch into master
git checkout master
git merge branch-name
```
