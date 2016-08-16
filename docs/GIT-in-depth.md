## Most common GIT questions and solutions

Borrowed from “[Most common git screwups/questions and solutions](http://41j.com/blog/2015/02/common-git-screwupsquestions-solutions/)”

```sh
# I wrote the wrong thing in a commit message
git commit --amend

# How can I undo the last commit?
git reset --hard HEAD~1

# To undo but keep working changes
git reset --soft HEAD~1

# Delete a git branch remotely
git push origin --delete branchname

# Remove all local untracked files (and directories) from local clone
# WARNING: You cannot undo this, so you should make a backup before doing this
git clean -f -d

# Clone all remote branches
git branch -a                                   # Check if branch is there
git checkout origin/branchname                  # Take a look at branch
git checkout -b branchname origin/branchname    # Create a local tracking branch

# Rename local branch
git branch -m oldname newname

# Revert to a previous git commit
git reset --hard commitid

# or, use soft to keep working items
git reset --soft commitid

# Remove a git submodule
git submodule deinit submodulename
git rm submodulename
git rm --cached submodulename
rm -rf .git/modules/submodulename

# Overwrite local files when doing a git pull
git fetch --all
git reset --hard origin/master

# Git export, exporting the source code as with “svn export”
git archive --format zip --output /full/path/to/zipfile.zip master

# Discard all my unchecked in changes
git checkout -- .

# Create a new remote branch from the current local one
git config --global push.default current
git push -u

# Restore a deleted file
# 1) Find the commit when file last existed
git rev-list -n 1 HEAD -- filename

# 2) Then checkout that file
git checkout deletingcommitid^ -- filename

# Revert a single file to a specific previous commit
git checkout commitid filename

# Make git ignore permissions/filemode changes
git config core.fileMode false

# Take a quick look at an old revision of a single file
git show commitid:filename
```

## Snippets

```sh
# Clone repository
git clone [address-to-git-repository]

# Update repository
git pull origin master

# Commit changes
git commit -am 'commit message'

# Push changes to live branch
git push origin master

# Git Upstream
git fetch upstream
git merge upstream/master

# View a list of files that were changed in the last commit
git show --pretty="format:" --name-only

# Remove cached DS_Store files
find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch

# Completely remove git ignored files from repo
git rm -r --cached .
git add .
git commit -am 'Remove cached ignored files'

# Delete remote tag
git tag -d 12345
git push origin :refs/tags/12345
```

## Create New Repository (local/server)

```sh
## On local machine
cd /path/to/new_project
git init
git add *
git commit -m "Initial commit"

## On git server (gitdev.geekrescue.com /home/git)
cd /home/git
sudo mkdir new_project.git
cd new_project.git
sudo git --bare init
sudo git config receive.denyNonFastforwards true
sudo chown -R git:git /home/git/

## Back to local machine (inside /path/to/new_project)
git remote add origin git@gitdev.geekrescue.com:new_project.git
git push -u origin master
```

## Reset to Previous Commit

```sh
# reset the index to the desired tree (example, <56e05fced>)
git reset 56e05fced

# move the branch pointer back to the previous HEAD
git reset --soft HEAD@{1}

git commit -m "Revert to 56e05fced"

# Update working copy to reflect the new commit
git reset --hard
```
