# Context switching between tasks

When working on multiple features or bug fixes simultaneously, it's important to switch between different branches and manage commits efficiently. Git offers several tools to help you transition smoothly between tasks, manage changes, and keep your commit history clean.

## git switch

The git switch command is used to switch between branches. It's a more intuitive alternative to git checkout for moving between branches and creating new ones.


```
git switch <branch>
# or
git switch -c <branch>
```

You can also use git stash to save your uncommitted changes when switching branches. This is particularly helpful when you need to switch tasks without losing your current progress.

```
git stash
git switch <branch>
git stash pop
```

`git checkout` is still available for switching branches, but `git switch` is recommended for its simplicity and clarity.

`git checkout` and `git switch` both allow you to switch between branches in Git, but git switch is a more specialized, user-friendly command introduced in Git 2.23 to reduce the complexity of git checkout. While git checkout can switch branches, create new ones, and even check out specific files, it has a broad range of behaviors that can sometimes be confusing. git switch focuses solely on changing branches, making it clearer and safer to use for that specific task. It offers simpler syntax for common operations like creating a new branch (git switch -c <branch-name>) or moving to an existing one (git switch <branch-name>).

## git rebase

`git rebase` is used to move or apply commits from one branch onto another, effectively "rebasing" the branch. It's often used to keep feature branches up to date with the latest changes from main without creating merge commits.

```bash
git switch feature-branch
git rebase main
```

## git merge

`git merge` is used to combine the changes from one branch into another. Unlike rebase, merge creates a new commit that records the merge. It's commonly used when you want to merge feature branches back into the main branch or a development branch.

```bash
git switch main
git merge feature-branch
```

Git will automatically create a merge commit if there are no conflicts. If conflicts arise, you will need to resolve them manually and complete the merge by committing the changes.

Merges are useful when you want to preserve the history of both branches, but they can lead to more complex commit graphs compared to rebase.

## git squash

Squashing commits combines multiple commits into a single one. This is often done before merging a feature branch into main to keep the commit history clean, especially if the branch contains many small or intermediate commits.

You can squash commits interactively during a rebase:

Start an interactive rebase:

```bash
git rebase -i HEAD~<n>
```

Replace <n> with the number of commits you want to squash. For example, to squash the last 3 commits:
```bash
git rebase -i HEAD~3
```

In the editor that opens, change pick to squash (or s) for the commits you want to squash:
```bash
pick abc123 Commit 1
squash def456 Commit 2
squash ghi789 Commit 3
```

You can also squash automatically when merging a feature branch:
```bash
git merge --squash <feature-branch>
```
