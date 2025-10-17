# Hide under the carpet - Use stashes to save the work in progress

In this challenge, you’ll practice using `git` stashes to temporarily “hide” your changes, switch tasks, and then bring everything back exactly as it was. You’ll create and manage multiple stashes, inspect them, and apply or drop them as needed.

Follow the steps below to master stashing:

1. Create and modify some files to simulate work in progress.
2. Stage a few files with git add, then stash everything using `git stash -m "your message"`.
3. Create several stashes by re-doing steps 1&2.
4. Check the stash stack with git stash list to see your saved work.
5. Show stash details using `git stash show` and `git stash show -p` for at least one stash.
6. Pop and apply stashes to bring your changes back into the working directory.
7. Selectively apply or drop specific stashes using their stash@{n} references.

[Guidelines and docs](../section/03-mastering-git-stash.md)
