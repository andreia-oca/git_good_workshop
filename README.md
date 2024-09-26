# Git Good - An essential guide to `git` Workshop

This repository contains the content for the Git Good workshop. The workshop is a collection of useful commands, tricks and workflows that I use in my day to day work as a software engineer. Each section is a markdown file in the `sections` directory. There you will find instructions, examples and commands to run based on a specific `git` topic.

## Prerequisites

You should have `git` installed on your machine.

Preferably, have a unix/linux/macOS machine. Windows users can use WSL.

Preferably, you should have a GitHub account (I am sure this workshop can work with other git providers as well, but these docs will be biased towards GitHub).

## Sections

Each section is a markdown file in the `sections` directory.
There you will find instruction, examples and commands to run based on a specific topic.

- [The usual git flow](sections/01-the-usual-git-flow.md) - clone/fork, create a branch, status, commit some changes, git status, git push
- [Make yourself at home](sections/02-make-yourself-at-home.md) - git config, git hist, git show, git diff
- [Mastering git stash](sections/03-mastering-git-stash.md) - git stash
- [Hot fixing in production](sections/04-hot-fixing-in-production.md) - git cherry-pick, git please
- [Code review shenanigans](sections/05-code-review-shenanigans.md) - git rebase -i, git commit -sv --amend, git commit -svm
- [Who dafaq wrote this - oh it's me](sections/06-who-dafaq-wrote-this-oh-its-me.md) - git blame, git bisect
- [Context switching between tasks](sections/07-context-switching-between-tasks.md) - git stash, git rebase, git merge, git squash
- [Advanced settings](sections/08-advanced-settings.md) - ssh key, pre-commit hooks

## Contributions

If you find a mistake, or you want to add a section, feel free to open an [issue](https://github.com/andreia-oca/git_good_workshop/issues) or fork this repository and open a [pull request](https://github.com/andreia-oca/git_good_workshop/fork).

## References

These references are dedicated to `git` geeks who want to check more in-depth configs about `git`.
They refer to advanced topics and the guts of `git`.
- So You Think You Know Git - FOSDEM 2024 https://www.youtube.com/watch?v=aolI_Rz0ZqY - nice tips and tricks from Scott Chacon
- Git's Best And Most Unknown Feature - https://www.youtube.com/watch?v=2uEqYw-N8uE - how to configure and use worktrees.
- You only Git Merge?!? feat Theo : DevHour #1 - https://www.youtube.com/watch?v=7gEbHsHXdn0 - git merge vs git rebase - what's best for big projects
- The guts of git - https://guts-of-git.carson-anderson.com/docs/workshop/ - git internals
