---
layout: default
title: Guide to Git
permalink: /resources/git-guide/
toc: true
---

Watch [Git Will Finally Make Sense After This](https://youtu.be/Ala6PHlYjmw) for an explanation of how git works. The guide below is for useful commands.

# Guide to Git

*This guide goes over the most important commands, see a full manual [here](https://wiki.archlinux.org/title/Git)*

## Add your GitHub account to PHGameStudio organization

- Share git username in group chat
- Confirm entering organization from email message

## Setup git CLI

- Go to GitHub → profile pic → settings → developer settings → personal access tokens → tokens (classic)
- Generate new token (classic)
- No expiration date
- Select scope write: packages
- Copy token (and save it somewhere if you don't have clipboard manager)

- `git config --global credential.helper store` to store account and password
- `git config --global user.email "email.name@email.com"`
- `git config --global user.name "github-username"`
- Clone/push a private repo using https connection and paste token

## Setup GitHub CLI

### Installation

- Windows: `winget install --id GitHub.cli`
- Mac OS: `brew install gh`
- Linux: use your package manager or same as Mac OS

### Authentication

- `gh auth login` to authenticate with your GitHub account
	- Select `GitHub.com`
	- Select `HTTPS` for preferred protocol
	- Select `Yes` to authenticate Git with your GitHub credentials
	- Select `Login with a web browser` and follow instructions
- `gh auth setup-git` to configure git to use your GitHub CLI credentials (replaces the need for manual PAT setup)

## Important commands

### Cloning a repository

- `git clone https://github.com/owner-name/existing-repo.git`
- `gh clone owner-name/existing-repo`
	- Only works for repos on GitHub
- `gh repo fork owner-name/existing-repo` to fork a repository and clone it locally
- `gh browse` to open the current repository in your web browser

### Creating a repository

- `git init`
- `git add file-1 file-2 dir`
- `git branch -m main`
- `git commit -am "commit message title" -m "commit message body"`
- `git remote add origin https://github.com/PHGameStudio/new-repo.git`
- `git push -u origin main`
- The last 2 lines can also be replaced with `gh repo create` and choosing "push an existing repository to GitHub" in the interactive repo creation menu

### Managing versions

- `git ls-files` to list tracked files under the working directory
- `git config --global alias.tree 'log --graph --oneline --all --decorate'`
- `git tree` to see a version tree\
	![](/images/git-tree-example.png){: width="75%"}

#### Linear versions

- *Commit hash* is the string shown before command message in the tree
	- `HEAD` can replace hash for representing current version
	- Use `HEAD~` for the version before `HEAD`
- `git checkout <commit-hash>` to view a commit (can't commit without checking out to newest)
- `git checkout <commit-hash> -- .` to do an "edit" that restores everything to a commit, can still commit afterwards and the commit will be after the commit before checkout
- `git diff <commit-hash-1> <commit-hash-2>` to see files changed between commits (commit-hash-2 is current version (HEAD) if blank)

#### Nonlinear versions - branches

- `git branch` to view name of all branches
- `git checkout branch-name` to checkout newest version in a branch
- `git checkout -b feature-branch` to create a new branch and switch to it
- `git checkout main`, `git merge feature` to merge branch `feature` into `main`
	- Make sure you commit all changes before checking out `main`
	- Some files may need to be resolved manually
- `git cherry-pick <commit-hash>` apply what changed in a specific commit to your current version (also may need manual resolution)
	- \*Cherry-pick a range of commits: `git cherry-pick <oldest-commit>^..<newest-commit>`

#### Working with remotes

- `git fetch` to fetch new commits on the remote, without changing current local version
- `git pull`: fetch and merge
	- May require manual conflict resolution, like when merging 2 local branches
- `git push -u origin main`: set origin/main as default remote and push local to remote. After this use `git push` to push to `main`, and `git push origin feature-branch` to push to a different branch

### Managing Pull Requests (PRs)

- `gh repo set-default` to set the base repository for PRs and issues (useful in forks)
- `gh pr create` to create a PR for your current branch
	- It will ask which repository to push to and which to use as the base
- `gh pr list` to see all open PRs
- `gh pr checkout <pr-number>` to checkout a PR locally
- `gh pr merge` to merge the current PR (interactive)
- `gh pr view --web` to see the PR in your browser

### Managing Issues

- `gh issue list` to see all open issues
- `gh issue create` to create a new issue (interactive)
- `gh issue view <issue-number> --web` to see the issue in your browser
- `gh issue close <issue-number>` to close an issue
