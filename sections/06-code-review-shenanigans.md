## Code reviews shenanigans

During the code review process, developers often need to make changes, rewrite commit histories, or clean up commits before merging. This section covers some common Git commands used to manage commits efficiently.

## Interactive rebase

The command `git rebase -i` allows you to clean up your commit history by combining, editing, or reordering commits interactively before pushing your changes. This is particularly useful when preparing code for review, as it keeps the commit history clean and understandable.

Run the following command to rebase the last few commits:

```bash
git rebase -i HEAD~<n>
```

An editor will open showing a list of your recent commits. You can now choose what to do with each commit:

* pick - Keep the commit as is.
* reword - Edit the commit message.
* edit - Edit the commit itself (message and content).
* squash - Combine this commit with the previous one.
* fixup - Similar to squash, but it discards the commit message.

A vim editor will open and you can change the action on each commit as you see fit. Once you save and save and close `vim` and `git` will checkout to each commit letting you make the changes you want.

```
edit abc123 Commit 1
reword def456 Commit 2
squash ghi789 Commit 3
```

For each commit check your surrounding first - you can run `git status`, `git diff`, `git hist` to understand the new context.

Sometimes, you want to modify the last commit (perhaps after receiving feedback during a review). The git commit --amend command allows you to amend the last commit, changing its contents or message. After running the command, an editor will open allowing you to modify the commit message. You can either leave it as is or update it based on your recent changes.


After you finished editing or rewording the commits, you can continue the rebase process by running the following commands:
```bash
# Add your changes to the staging area
git add <files>
# Append the changes to the last commit
git commit -sv --amend
# Continue the rebase process
git rebase --continue
```

When you amend a commit or rebase, Git rewrites the commit history. To push these changes, you need to force-push, as the history of your local branch will differ from the remote branch. However, it's important to do this safely, and --force-with-lease helps prevent overwriting commits pushed by others.

```bash
git please <origin> <branch>
# or
git push --force-with-lease <origin> <branch>
```

## Test around

1. Create multiple commits: Make several small changes and commit them individually in a local `git` repository.
2. Interactive rebase: Use `git rebase -i HEAD~<n>` to reorder, squash, or edit commits. Change commit messages and test squashing related commits into one.
3. Amend a commit: After making a small change, use `git commit --amend` to update the last commit with the new changes or modify its message.
4. Force push safely: After rebasing or amending commits, try to `git push`.
5. Use `git please` or `git push --force-with-lease` to push changes and ensure you're not overwriting remote commits.
