# Git Workflow Summary

This file summarizes the basic Git workflow, from initializing a repository to pushing it to a remote server.

## 1. Initialization

### `git init`
- **Purpose:** To create a new Git repository.
- **How it works:** It creates a hidden `.git` directory in your current folder. This directory contains all the necessary files and metadata for Git to track your project's history.

## 2. Checking the Status

### `git status`
- **Purpose:** To see the current state of your repository.
- **What it shows:**
    - Which files are modified.
    - Which files are "staged" (ready to be committed).
    - Which files are "untracked" (new files that Git doesn't know about yet).

## 3. Staging Changes

### `git add <file>`
- **Purpose:** To add file changes to the "staging area". The staging area is a snapshot of the changes you want to include in your next commit.
- **Keywords:**
    - `add`: The command to stage changes.
    - `<file>`: The name of the file you want to stage. You can also use `.` to stage all modified and new files in the current directory.

## 4. Committing Changes

### `git commit -m "Your commit message"`
- **Purpose:** To save your staged changes to the project's history. A commit is a permanent snapshot of your project at a specific point in time.
- **Keywords:**
    - `commit`: The command to create a new commit.
    - `-m`: A flag that stands for "message". It allows you to provide a commit message directly from the command line.
    - `"Your commit message"`: A brief description of the changes you made.

## 5. Viewing History

### `git log`
- **Purpose:** To see the history of commits in your repository.
- **What it shows:** A list of all commits, with their unique ID (hash), author, date, and commit message.

### `git diff`
- **Purpose:** To see the exact changes you've made to your files since the last commit.
- **How it works:** It shows the differences between your working directory and the last commit.

## 6. Working with Remotes

### `git remote add <name> <url>`
- **Purpose:** To connect your local repository to a remote repository (e.g., on GitHub).
- **Keywords:**
    - `remote`: The command for managing remote connections.
    - `add`: The subcommand to add a new remote.
    - `<name>`: A nickname for the remote repository. `origin` is the standard convention.
    - `<url>`: The URL of the remote repository.
- **Example:** `git remote add origin https://github.com/RohitBind123/git-test.git`

### `git remote -v`
- **Purpose:** To list all the remote repositories you have configured.
- **Keywords:**
    - `-v`: A flag that stands for "verbose". It shows the URLs for each remote.

## 7. Pushing Changes

### `git push -u <remote> <branch>`
- **Purpose:** To upload your committed changes from your local branch to a remote repository.
- **Keywords:**
    - `push`: The command to upload changes.
    - `-u`: A flag that stands for `--set-upstream`. It creates a link between your local branch and the remote branch. This allows you to use `git push` (without arguments) in the future.
    - `<remote>`: The name of the remote you're pushing to (e.g., `origin`).
    - `<branch>`: The name of the branch you're pushing (e.g., `master`).
- **Example:** `git push -u origin master`
