# Git & GitHub Foundations Lab

## Lab Overview

In this hands-on lab, you will practice a basic Git and GitHub workflow
by creating a feature branch, updating repository files, committing your
changes, pushing the branch to GitHub, and completing a pull request.

**Estimated time:** 30--45 minutes\
**Difficulty:** Beginner

## Learning Objectives

By the end of this lab, you will be able to:

-   Create and switch to a feature branch.
-   Update an existing `.gitignore` file.
-   Edit a `README.md` file using Markdown.
-   Stage and commit changes with Git.
-   Push a local branch to GitHub.
-   Open a pull request (PR) on GitHub.
-   Merge a pull request.

## Prerequisites

Before you begin, make sure you have:

-   Git installed on your computer.
-   A GitHub account.
-   The lab repository URL provided by your instructor.
-   Your own fork of the lab repository.
-   Your fork cloned to your local computer.
-   A terminal, command prompt, or Git Bash.
-   A text editor or IDE.

> **Important:** Do **not** start working in a direct clone of the
> instructor's repository. First fork the repository into your own
> GitHub account, then clone your fork. The steps below use `origin` for
> the fork you own.

## Before You Start | Fork the Repository

**Goal:** Create a personal copy of the lab repository and work from
that copy instead of the instructor-owned repository.

1.  Open the lab repository URL provided by your instructor.

2.  Select **Fork** near the top-right of the GitHub page.

3.  Choose your personal GitHub account as the owner, and create the fork.

4.  Open your fork at
    `https://github.com/YOUR-USERNAME/lab-repository-name`.

5.  Select **Code** and copy the HTTPS URL for your fork.

6.  Clone **your fork**, not the instructor-owned repository:

    ``` bash
    git clone https://github.com/YOUR-USERNAME/lab-repository-name.git
    cd lab-repository-name
    ```

7.  Confirm that `origin` points to your fork:

    ``` bash
    git remote -v
    ```

    The `fetch` and `push` URLs shown for `origin` should contain
    `YOUR-USERNAME`.

> **Checkpoint:** You have forked the repository and cloned your fork.
> Do not continue until `origin` points to your GitHub account.

## Initial Check

1.  Open a terminal.

2.  Change to your cloned repository directory:

    ``` bash
    cd path/to/your-repository
    ```

3.  Confirm that you are in the correct repository:

    ``` bash
    git status
    ```

4.  Check the current branch:

    ``` bash
    git branch
    ```

If your working tree contains changes you need to keep, commit or safely
set them aside before starting. Do not overwrite someone else's work.

------------------------------------------------------------------------

## Lab Step 1 \| Create a Feature Branch

**Goal:** Create a separate branch for your lab work so that your
changes do not go directly onto the default branch.

1.  Update your view of the remote repository:

    ``` bash
    git fetch origin
    ```

2.  Switch to the repository's default branch. The default branch is
    commonly named `main`:

    ``` bash
    git switch main
    ```

    If your repository uses a different default branch, use that branch
    name instead.

3.  Bring your local default branch up to date:

    ``` bash
    git pull origin main
    ```

4.  Create and switch to a new feature branch:

    ``` bash
    git switch -c feature/git-github-foundations
    ```

5.  Verify that the feature branch is active:

    ``` bash
    git branch
    ```

    The active branch is marked with an asterisk (`*`).

**Checkpoint:** You are working on `feature/git-github-foundations`, not
directly on `main`.

------------------------------------------------------------------------

## Lab Step 2 \| Modify Existing `.gitignore`

**Goal:** Add common generated or local-only files to the repository's
existing ignore rules.

1.  Locate the existing `.gitignore` file in the repository's root
    directory.

2.  Open it in your text editor.

3.  Review its current entries. **Do not delete existing rules.**

4.  Add the following entries if they are not already present:

    ``` gitignore
    # Operating system files
    .DS_Store
    Thumbs.db

    # Editor and IDE settings
    .vscode/
    .idea/

    # Temporary and log files
    *.log
    *.tmp

    # Environment variables and local secrets
    .env
    .env.local
    ```

5.  Save the file.

**Important notes:**

-   `.gitignore` prevents matching **untracked** files from being
    included in Git's normal status and staging workflow.
-   If a file is already tracked by Git, adding it to `.gitignore` does
    not automatically stop tracking it.
-   Never commit passwords, API keys, tokens, or other secrets.

**Checkpoint:** The existing `.gitignore` has been updated without
removing its original rules.

------------------------------------------------------------------------

## Lab Step 3 \| Edit `README.md`

**Goal:** Update the repository's README with a short description of
your practice work.

1.  Open the existing `README.md` in the repository root.

2.  Preserve useful existing project information.

3.  Add a section like the following. Adapt the wording to match your
    repository:

    ``` markdown
    ## Git and GitHub Foundations Lab

    This repository includes practice work for learning the Git and GitHub workflow.

    ### Skills Practiced

    - Creating and switching to a feature branch
    - Updating `.gitignore`
    - Editing Markdown documentation
    - Staging and committing changes
    - Pushing a branch to GitHub
    - Opening and merging a pull request
    ```

4.  Save the file.

**Checkpoint:** `README.md` contains the new lab section and any
original content you chose to retain.

------------------------------------------------------------------------

## Lab Step 4 \| Stage and Commit

**Goal:** Review your changes, stage the intended files, and create a
commit.

1.  Check which files have changed:

    ``` bash
    git status
    ```

2.  Review the changes before staging:

    ``` bash
    git diff
    ```

3.  Stage the two files you updated:

    ``` bash
    git add .gitignore README.md
    ```

4.  Confirm what is staged:

    ``` bash
    git status
    git diff --staged
    ```

5.  Commit the changes with a clear message:

    ``` bash
    git commit -m "Update gitignore and README for foundations lab"
    ```

6.  Confirm that the commit was created:

    ``` bash
    git log -1 --oneline
    ```

**Checkpoint:** Your changes are committed locally on the feature
branch.

------------------------------------------------------------------------

## Lab Step 5 \| Push to GitHub

**Goal:** Publish your feature branch to the remote GitHub repository.

1.  Push the feature branch and set its upstream:

    ``` bash
    git push -u origin feature/git-github-foundations
    ```

2.  Open the repository on GitHub in your web browser.

3.  Confirm that GitHub shows your recently pushed branch. GitHub may
    also display a prompt to create a pull request.

**If the push fails:**

-   Confirm that you have internet access.

-   Confirm that `origin` points to the correct GitHub repository:

    ``` bash
    git remote -v
    ```

-   Confirm that you are on the expected branch:

    ``` bash
    git branch
    ```

-   If Git reports that authentication is required, complete the
    authentication flow configured for your Git installation (for
    example, GitHub CLI, a credential manager, or SSH).

**Checkpoint:** Your feature branch is visible on GitHub.

------------------------------------------------------------------------

## Lab Step 6 \| Open a Pull Request on GitHub

**Goal:** Request that your feature branch changes be reviewed and
merged into the default branch.

1.  Open your repository on GitHub.

2.  Select **Pull requests**.

3.  Select **New pull request**.

4.  Set the branches:

    -   **Base:** `main` (the branch you want to merge into).
    -   **Compare:** `feature/git-github-foundations` (the branch
        containing your changes).

5.  Review the changed files and confirm that the correct changes are
    included.

6.  Select **Create pull request**.

7.  Enter a title, such as:

    `Update gitignore and README for foundations lab`

8.  Add a description, such as:

    ``` markdown
    ## Summary
    - Updated the existing .gitignore with common local and temporary files.
    - Added a Git and GitHub foundations section to README.md.

    ## Testing
    - Reviewed the staged changes before committing.
    - Confirmed the feature branch was pushed to GitHub.
    ```

9.  Select **Create pull request** to submit it.

**Checkpoint:** The pull request is open, and its base and compare
branches are correct.

------------------------------------------------------------------------

## Lab Step 7 \| Merge the Pull Request

**Goal:** Merge the reviewed feature branch into the repository's
default branch.

1.  Open the pull request you created.
2.  Review the conversation and **Files changed** tab.
3.  If your repository requires approvals or automated checks, wait for
    the required approvals and checks to pass.
4.  When GitHub enables the merge action, select **Merge pull request**.
5.  Confirm the merge by selecting **Confirm merge**.
6.  Verify that GitHub marks the pull request as **Merged**.
7.  Optionally select **Delete branch** on GitHub after the merge. This
    deletes the remote feature branch, not your local branch.

**Checkpoint:** The pull request is merged into `main`.

### Update Your Local Repository

After the merge, update your local default branch:

``` bash
git switch main
git pull origin main
```

If you want to remove your local feature branch after confirming it has
been merged:

``` bash
git branch -d feature/git-github-foundations
```

------------------------------------------------------------------------

## Lab Completion Checklist

Use this checklist to confirm that you completed the workflow.

-   [ ] Forked the instructor's repository into my GitHub account.
-   [ ] Cloned my fork and confirmed that `origin` points to my account.
-   [ ] Created `feature/git-github-foundations`.
-   [ ] Modified the existing `.gitignore` without removing its original
    rules.
-   [ ] Edited `README.md` and preserved relevant existing content.
-   [ ] Reviewed, staged, and committed the intended files.
-   [ ] Pushed the feature branch to GitHub.
-   [ ] Opened a pull request with the correct base and compare
    branches.
-   [ ] Reviewed and merged the pull request.
-   [ ] Updated the local `main` branch after the merge.

## Knowledge Check

Answer these questions in your own words:

1.  Why is it useful to create a feature branch instead of making
    changes directly on `main`?
2.  What is the purpose of a `.gitignore` file?
3.  What is the difference between `git add` and `git commit`?
4.  What does `git push` do?
5.  What are the base and compare branches in a pull request?
6.  Why might a pull request require reviews or status checks before it
    can be merged?
7.  After a pull request is merged on GitHub, why should you run
    `git pull` on your local `main` branch?

## Useful Git Commands Reference

  ---------------------------------------------------------------------
  Command                            Purpose
  ---------------------------------- ----------------------------------
  `git status`                       Show the current branch and
                                     working-tree status

  `git fetch origin`                 Download remote updates without
                                     merging them

  `git switch main`                  Switch to the `main` branch

  `git pull origin main`             Fetch and integrate updates from
                                     remote `main`

  `git switch -c branch-name`        Create and switch to a new branch

  `git diff`                         Show unstaged changes

  `git add file-name`                Stage a file

  `git diff --staged`                Show staged changes

  `git commit -m "message"`          Create a commit

  `git push -u origin branch-name`   Push a branch and set its upstream

  `git log -1 --oneline`             Show the latest commit
  ---------------------------------------------------------------------

## Lab Finished

Congratulations! You have practiced the core Git and GitHub
collaboration workflow:

**Fork → Clone → Branch → Edit → Stage → Commit → Push → Pull Request →
Merge**

You can repeat this workflow whenever you contribute a change to a
shared repository.
