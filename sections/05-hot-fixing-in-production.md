# Hot fixing in production

In production environments, version control systems like Git are critical for tracking changes, compiling, building, and deploying code safely.

Typically, the lifecycle of a change looks like this:
* Create a Pull Request (PR): The change is proposed through a PR, which is then reviewed by peers.
* Merge into dev/staging: Once approved, the PR is merged into a development or staging branch, where it undergoes automated and manual testing.
* Release to main: After passing all tests, the changes are merged into the main branch and deployed to production.

## Hotfixing with cherry-picking

If a critical bug arises in production and you need to fix it immediately, you can't merge your entire working branch into main, as it might include unfinished or untested changes. Instead, you'll use cherry-picking to isolate the commit that contains the bug fix.

Run `git log` or `git hist` to display the history of commits. Locate the specific commit you want to cherry-pick. Each commit is listed with its SHA (a long alphanumeric identifier).

Once you have the commit SHA, switch to the branch where the fix is needed (usually main or a hotfix branch). Then run:

```bash
git cherry-pick <commit-sha>
```

This will apply the changes from the commit to your current branch.

If there are merge conflicts, `git` will pause the process and notify you. You will need to manually resolve the conflicts. Once resolved, continue the cherry-pick process by running:

```bash
git cherry-pick --continue
```

If things go wrong or you decide not to apply the changes, you can abort the cherry-pick with:

```bash
git cherry-pick --abort
```

Once the cherry-pick is complete, you can push the changes to the remote repository:

```bash
git push
```

## Switch branches with git switch

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

Note: `git checkout` and `git switch` both allow you to switch between branches in Git, but git switch is a more specialized, user-friendly command introduced in Git 2.23 to reduce the complexity of git checkout. While git checkout can switch branches, create new ones, and even check out specific files, it has a broad range of behaviors that can sometimes be confusing. git switch focuses solely on changing branches, making it clearer and safer to use for that specific task. It offers simpler syntax for common operations like creating a new branch (git switch -c <branch-name>) or moving to an existing one.

## Test around

1. Create New Branches: Create two or more new branches from the main branch.
2. Make Changes and Commit: Make a change in each branch and commit those changes.
3. Cherry-Pick a Commit: Cherry-pick a commit from one branch and apply it to another branch.
4. Make Multiple Commits: In one of the branches, create multiple commits to simulate more extensive work.
5. Hot-Fixing: Cherry-pick a specific commit that contains a hotfix and apply it to the main branch.
6. Push Changes to Remote: Push all the changes to the remote repository.
7. Verify on GitHub: Check the remote repository on GitHub to confirm that your changes have been applied successfully.
