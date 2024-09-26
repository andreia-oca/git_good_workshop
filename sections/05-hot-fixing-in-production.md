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
