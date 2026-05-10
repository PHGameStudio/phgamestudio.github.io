---
layout: default
title: Guide to Jujutsu (jj)
permalink: /resources/jj-guide/
toc: true
---

Check out the [Jujutsu Tutorial](https://martinvonz.github.io/jj/latest/tutorial/) for an explanation of how it works. The guide below is for useful commands.

# Guide to Jujutsu

Jujutsu (`jj`) is a version control system that's more intuitive and efficient than Git for local development. It is designed to work seamlessly with Git as a backend, allowing you to use `jj` for your personal workflow while collaborating with others via Git and GitHub. This makes it ideal for multi-device sync or contributing to team projects without forcing everyone to switch from Git.

_This guide goes over the most important commands, see the full manual [here](https://martinvonz.github.io/jj/latest/)_

## Setup jj CLI

- `jj config set --user user.name "Your Name"`
- `jj config set --user user.email "your.email@example.com"`

### Git integration setup

- Ensure you have `git` and `gh` set up as described in the [Git Guide](/resources/git-guide/)
- `jj` works best when it can find your git credentials.

## Important commands

_Most `jj` commands have shorthands (e.g., `jj b s` for `jj bookmark set`). You can shorten any command as long as it's unambiguous._

### Cloning a repository

- `jj git clone https://github.com/owner-name/existing-repo.git`
- `jj git clone owner-name/existing-repo` (if using the git backend)

### Creating a repository

- `jj init --git` to create a new jj repo with a git backend
- `jj git init --colocate` to turn an existing git repo into a jj repo (keeping the `.git` folder)

### Managing versions

- `jj log` to see the version tree (jj's log is much more readable by default)
- `jj status` or `jj st` to see current changes

#### The jj Workflow

Unlike Git, `jj` doesn't have a staging area. Your working copy is always an "open" commit.

- _Change ID_ (usually 4-8 letters like `qpvz`) is **stable**. It stays the same even if you rebase or edit the commit. Use this for most commands.
- _Commit ID_ (hex like `a1b2`) changes whenever you modify a commit.

- `jj describe -m "commit message"` to set the message of the current working commit.
- `jj new` to "finish" the current commit and start a new one on top of it.
- `jj edit <change-id>` to go back and edit a previous commit.
- `jj squash` to move changes from the current commit into its parent.
- `jj abandon` to discard the current change.
- `jj undo` to undo the last command you ran.

### Handling Conflicts

In `jj`, conflicts are "first-class citizens." They don't stop you from working or committing.

- When a conflict occurs, `jj` will show it in `jj log` and `jj status`.
- You can still run `jj new`, `jj rebase`, etc., even with conflicts.
- **To resolve:** Open the conflicted file, fix the markers, and save. `jj` will detect the fix automatically.

#### Better Editor Compatibility

By default, `jj` uses its own conflict format. To use Git-style markers (which most editors like VS Code highlight correctly), run:

- `jj config set --user ui.conflict-marker-style "git"`

#### Nonlinear versions - Bookmarks (Branches)

In `jj`, branches are called **bookmarks**. They don't move automatically; you point them to where you want them.

- `jj bookmark list` to see all bookmarks.
- `jj bookmark set feature-name` to point a bookmark to the current commit.
- `jj bookmark delete feature-name` to remove a bookmark.

#### Working with remotes & GitHub

- `jj git fetch` to fetch from the remote.
- `jj rebase -d main@origin` to move your current work on top of the remote main.
- `jj bookmark track bookmark-name --remote origin` to track a remote bookmark locally.
- `jj git push --bookmark feature-name` to push a specific bookmark to GitHub.
  - Subsequent `jj git push` will update the bookmark on the remote if it has moved locally.

### Managing Pull Requests

- Use `gh pr create` as usual. `jj` will often print the PR creation link after a push.
- To update a PR, just edit your commits and `jj git push`.
