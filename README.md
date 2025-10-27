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

## 8. Working with Branches

Branches allow you to work on different features or fixes in isolation without affecting the main `master` branch.

### Scenario 1: Creating a New Branch Locally

This is the most common way to start new work.

1.  **Create and switch to a new branch:**
    ```bash
    git checkout -b <your-branch-name>
    ```
    *   This single command creates a new branch from your current branch and immediately switches to it.

2.  **Make your changes:**
    *   Modify your code, create new files, etc.

3.  **Add and commit your changes:**
    ```bash
    git add .
    git commit -m "Add new feature"
    ```

4.  **Push the new branch to the remote:**
    *   The first time you push a new branch, you need to set the "upstream" link.
    ```bash
    git push -u origin <your-branch-name>
    ```
    *   After this initial push, you can simply use `git push` for subsequent changes on this branch.

### Scenario 2: Branch Created on GitHub

If a branch is created directly on GitHub, you need to bring it to your local machine.

1.  **Fetch all remote changes:**
    *   This command downloads information about new branches from the remote repository without changing your local files.
    ```bash
    git fetch origin
    ```

2.  **Switch to the desired branch:**
    *   Git is smart. If you try to checkout a branch that exists on the remote but not locally, it will create a local copy for you and set it up to track the remote one.
    *   As an example, we used this to checkout the `new-test-branch` that was created on GitHub:
    ```bash
    git checkout new-test-branch
    ```

3.  **Make, add, and commit changes:**
    *   This process is the same as always.
    ```bash
    git add README.md
    git commit -m "Update README on new branch"
    ```

4.  **Push your changes:**
    *   Because the tracking relationship was already set up in the checkout step, you can just use the simple push command.
    ```bash
    git push
<<<<<<< HEAD
    ```

## 9. Other Important Concepts

Here are a few other essential commands and concepts for using Git effectively.

### Updating Your Local Repository (`git pull`)

If other people are pushing changes to the remote repository, your local version will become outdated. `git pull` updates your current local branch with any new commits from the corresponding remote branch.

```bash
git pull origin master
```
*   This fetches the changes from the `master` branch on the `origin` remote and merges them into your current local branch. It's a combination of `git fetch` and `git merge`.

### Merging Branches (`git merge`)

Once you have finished working on a feature in a separate branch, you'll want to merge it back into your main branch (e.g., `master`).

1.  **Switch to the branch you want to merge into:**
    ```bash
    git checkout master
    ```
2.  **Run the merge command:**
    ```bash
    git merge <your-feature-branch>
    ```
*   This takes all the commits from `<your-feature-branch>` and integrates them into the `master` branch.

### Resolving Merge Conflicts

Sometimes, Git cannot automatically merge changes because the same lines of a file were changed on both branches. This is a **merge conflict**.

*   Git will mark the conflicted areas in the file like this:
    ```
    <<<<<<< HEAD
    // Code from your current branch
    =======
    // Code from the other branch
    >>>>>>> <other-branch-name>
    ```
*   To resolve the conflict, you must:
    1.  Open the file.
    2.  Manually edit the code to keep the changes you want.
    3.  Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
    4.  Save the file.
    5.  `git add` the resolved file.
    6.  `git commit` to finalize the merge.

### Ignoring Files (`.gitignore`)

You often have files or directories that you don't want Git to ever track (e.g., log files, dependency folders like `node_modules`, build outputs).

*   Create a file named `.gitignore` in the root of your repository.
*   Add the names of files or folders you want to ignore, one per line.
*   Example `.gitignore` content:
    ```
    # Ignore dependency folders
    node_modules/

    # Ignore log files
    *.log

    # Ignore environment variables file
    .env
    ```

### Undoing Changes (A Quick Guide)

*   **Discard changes in a file (before staging):** To revert a file to how it was at the last commit.
    ```bash
    git checkout -- <file-name>
    ```
*   **Unstage a file (before committing):** To remove a file from the staging area.
    ```bash
    git reset HEAD <file-name>
=======
>>>>>>> aeafd0dd624c3a4dfeb7d5e0fab7a58c8e848c9f
    ```