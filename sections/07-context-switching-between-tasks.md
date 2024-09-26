# Context switching between tasks

When working on multiple features or bug fixes simultaneously, it's important to switch between different branches and manage commits efficiently. Git offers several tools to help you transition smoothly between tasks, manage changes, and keep your commit history clean.

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

## Test around

1. Rebase a Feature Branch: On one of the feature branches, run git rebase main to apply the latest changes from the main branch and keep the feature branch up to date.
2. Merge a Feature Branch: Switch to the main branch and use git merge <feature-branch> to combine changes, observing how Git handles merge commits.
3. Squash Commits During Rebase: Perform an interactive rebase with `git rebase -i HEAD~<n>` on a feature branch, squashing several commits into one to clean up the commit history.
4. Automatic Squashing on Merge: Merge a feature branch into the main branch using `git merge --squash <feature-branch>` to see how Git combines commits without creating a merge commit.
5. Push Changes to Remote: After making changes, push your branches to the remote repository to verify that the history is clean and structured as expected.
