# Who wrote this - oh it's me

Git provides several powerful commands to track down who made changes, investigate when bugs were introduced, and revert or modify commits. Let's explore the most important ones for these tasks:

## Git blame

The git blame command shows who made the last modification to each line of a file, providing a line-by-line history. It’s particularly useful when you want to find out who introduced a certain change.

```
git blame <file>
```

Output:
```
abc123 (Andreia Ocanoaia 2023-09-15 10:15:00) def some_function():
def456 (Jane Smith 2023-09-16 09:12:00)       return "hello world"
```

## Git bisect

`git bisect` is used to find the commit that introduced a bug by performing a binary search across the commit history. This is useful when you know a bug exists but aren't sure when it was introduced.

Start a bisect session:

```bash
git bisect start
```

Tell Git a good (non-buggy) commit:

```bash
git bisect good <commit-sha>
```

Tell Git a bad (buggy) commit (usually the latest commit):

```bash
git bisect bad <commit-sha>
```

Git will then check out a commit halfway between the good and bad ones.
You can run commands and test if the bug is present in this commit.

If the commit is good, run:
```bash
git bisect good
```

If the commit is bad, run:

```bash
git bisect bad
```

Git will repeat the process, narrowing down to the commit that introduced the bug.

Once found, end the session:

```bash
git bisect reset
```

## Git log

The git log command shows the commit history of a repository. It can be used with various options to show the commit details, including author, commit message, and date.

```bash
git log
# or
git log --oneline
# or
git log --oneline --graph
```

## Git show

git show displays detailed information about a specific commit, including the diff of what was changed.

```bash
git show
# or
git show <commit-sha>
```

## Git diff

The git diff command shows the differences between two commits, two branches, or the working directory and the index. It’s used to view changes before committing or comparing versions of files.

```bash
git diff
# or
git diff --cached
# or
git diff <commit-sha> <commit-sha>
```

## Git reset

The git reset command is used to undo changes by resetting the current HEAD to a specified commit. There are different modes of resetting, depending on how much you want to undo.

```bash
git reset --soft <commit-sha>
# or
git reset --mixed <commit-sha>
# or
git reset --hard <commit-sha>
```

## Git revert

git revert is a safer way to undo a commit because it creates a new commit that undoes the changes, instead of altering the commit history like git reset. It's useful when you need to undo a commit that has already been pushed to a shared branch.

```bash
git revert <commit-sha>
```

This creates a new commit that undoes the changes introduced by the specified commit.

## Test around

To practice these commands, you can clone a repository with more contributors and larger history such as the one used for the demo.
1. Clone a repository with multiple contributors.
```
git clone https://github.com/genez-io/genezio
```
2. Use git blame: Select a file of interest and use `git blame <file>` to see who last modified each line. Identify the author of a specific change that you're curious about.
3. Perform a Bisect - try to find the commit where genezio has the version 2.6.0 (check `package.json` for the version).
    * Start a bisect session with git bisect start.
    * Mark a known good commit with git bisect good <commit-sha>.
    * Mark a known bad commit with git bisect bad <commit-sha>.
    * Test the commits as Git checks them out, running git bisect good or git bisect bad until you find the commit that introduced the bug.
    * Reset the bisect session with git bisect reset once done.
4. View Commit History with git log: Use `git log`, `git hist`, `git show` and its various options to explore the commit history.
5. Revert a Commit: Revert a commit using `git revert` and observe how it creates a new commit that undoes the changes.
