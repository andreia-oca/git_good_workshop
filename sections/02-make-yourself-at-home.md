# Make yourself at home - git config

`git` is very configurable and extendable. To adjust it to your needs, you can configure it with the `git config` command or in `~/.gitconfig` file.

Configure the following settings on your machine.
The workshop will rely on them from now on.

### Name and email

Set your name and email address globally:

In the `~/.gitconfig` file add the following lines:

For example:
```bash
[user]
	name = <Your Name>
	email = <Your Email>
```

This is useful to sign your commits with your name and email address.
This way you can be later identified as the author of the commit.

The same can be done with the `git config` command:

```bash
git config --global user.name "<Your Name>"
git config --global user.email "<Your Email>"
```

### Aliases

Aliases are shortcuts for complex `git` commands.

In practice, these aliases make using Git more efficient by reducing the amount of typing and providing clearer log outputs.

```
[alias]
    co = checkout
    please = push --force-with-lease
    hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
    hist-long = log --pretty=format:'%h %ad | %s%d [%an]' --graph
    bb = !~/better-git-branch.sh
```

1. `co = checkout`

This sets a shortcut for the git checkout command. Instead of typing git checkout (which can be long), you can simply use git co to switch branches or check out files.

Example:

```bash
git co main  # Equivalent to git checkout main
```

2. please = push --force-with-lease

This creates an alias for `git push --force-with-lease`. `--force-with-lease` is a safer alternative to --force because it ensures you're only forcing the push if no one else has pushed to the branch since your last pull.

Using `git please` essentially lets you force-push changes without accidentally overwriting someone else's work.

Example:

```bash
git please main my-branch # Equivalent to git push --force-with-lease main my-branch
```

3. git hist
This creates a customized log view showing the commit history in a clean, concise format. Here's what the format shows:
The log is also displayed as a graph, visually showing the branching history.

Example:

```bash
git hist  # Shows a compact, graphical commit history
```

4. git hist-long

This is similar to the `git hist` but allows the developer to see more commits by appending the `-n <number>` flag to the `git hist-long` command.

Example:

```bash
git hist-long -n 30 # Shows a commit history with the last 30 commits
```

5. git bb

This alias runs an external shell script called better-git-branch.sh. The exclamation mark (!) tells Git to run a shell command instead of a Git command. The script enhances the output of the `git branch` command by ordering branches by the last commit date.

This is useful when you have many local branches and you want to switch to the most recent one.

Example:

```bash
git bb  # Runs the better-git-branch.sh script\
```

To run the script, you need to create a file called `better-git-branch.sh` in your home directory and make it executable.
The script can be content can be found here: [better-git-branch.sh](https://gist.github.com/schacon/e9e743dee2e92db9a464619b99e94eff).

You can play with it - create multiple branches and commits to them and then run `git bb` to see the branches ordered by the last commit date.

```bash
### Other configurations

This disables the pager for the git log, git branch, git diff, and git show commands, ensuring output is shown directly in the terminal without paging. It is useful to release your terminal without having to press `q` to exit the pager.

To experiment with it, you can try to run `git log` in the repository you have cloned before and after adding this configuration.
```
[pager]
	log = false
	branch = false
	diff = false
	show = false
```

This automatically sets up the remote tracking branch for new branches when pushing for the first time, reducing the need for manual setup. Before this configuration, you would have to run `git push --set-upstream origin <branch-name>` to set up the remote tracking branch. Now you can just run `git push` and it will set automatically be set up for you.
```
[push]
	autoSetupRemote = true
```

This sets the default text editor for Git to `vim`.
```
[core]
    editor = vim
```

This sets the default branch name to main when initializing a new Git repository, instead of using master.
```
[init]
	defaultBranch = main
```

You are all set up! Now you can use these configurations in your day-to-day work with `git`.

## Add your git alias here

If you have a favourite `git` configuration or alias that you would like to share, feel free to open a pull request with it.
I would love to see more tips and tricks from the community and the workshop will benefit from it as well <3.
