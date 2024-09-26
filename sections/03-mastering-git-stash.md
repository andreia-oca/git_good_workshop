# Mastering git stages and git stash

There are 4 places where your files can be in Git:
* staging area - they are going to be committed
* tracking area - the changes made to those files is tracked
* untracked files - the changes are not tracked
* stashed files - the changes are saved for later use in a separate stack

The stash is a powerful feature in Git that allows you to save changes that you are not ready to commit. This is useful when:
* you want to switch branches or work on a different task without committing your changes.
* you want to rebase or pull changes from the remote repository without committing your changes and git won't let you do it because you have uncommitted changes.
* you want to save experimental work that you are not sure you want to keep.

## Navigate a file through the stages

To add a file to the staging area, you can run:
```bash
git add <file>
```

`git` is great because (almost) every command is revertable and you can easily go back to a previous state if you messed up.
To revert changes made to a file in the staging area, you can run:
```bash
git restore --staged <file>
```

To revert changes made to a file in the working directory, you can run:
```bash
git restore <file>
```
This will bring the file back to the state it was in the last commit and drop all changes made to it.

## Stashing changes

To stash changes, run the following command:
```bash
git stash
```

The stashes are assigned a description/name automatically. It's useful to write a specific message when stashing changes. You can do this by running:
```bash
git stash -m "my experimental work on feature X"
```

This command will stash all the changes in your working directory and index. The changes will be saved in a stack and removed from your working directory.

You can stash specific files by running:
```bash
git stash push <list_of_files>
```

You can see the stashes and their unique identifiers and messages by running:
```bash
git stash list
```

You can even show the contents of a stash by referencing it with the stash@{n} syntax, where n is the number associated with the stash. For example, to show the contents of the first stash, you would run:
```bash
# List only the filenames in the stash
git stash show stash@{0}
```

or

```bash
# List the filenames and the changes made in the stash
git stash show -p stash@{0}
```

The stashes work on FIFO (first-in-first-out) approach.

To retrieve the last stash and remove it from the stack, you can run:
```bash
git stash pop
```

To retrieve the last stash and keep it in the stack, you can run:
```bash
git stash apply
```

If you want to retrieve a specific stash, you can reference it by running:
```bash
git stash pop stash@{n}
```

If you decide that you don't want to keep the stash, you can remove it by running:
```bash
git stash drop stash@{n}
```

Stashes will save you out of pickle a lot of times. They are a great way to save your work and come back to it later.

## Test around

1. Create and Modify Files: Create several files and make changes to them to simulate work in progress.
2. Add Files to the Staging Area: Use git add to stage the modified files, preparing them for a commit.
3. Stash Changes: Stash the changes using git stash to save your work without committing.
4. Retrieve Stashed Changes: Use `git stash pop` to retrieve and apply the stashed changes back to your working directory.
5. Create Multiple Stash Entries: Repeat the process to create additional stash entries with different files and messages.
6. Show Stash Contents: Use git stash list to view the stashed entries and their associated messages.
7. Retrieve or Drop Stashes: Retrieve specific stashes using `git stash apply <stash@{n}>` or drop unwanted stashes using `git stash drop <stash@{n}>`.
