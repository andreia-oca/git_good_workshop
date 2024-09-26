# The usual git flow

In this section, we will cover the most common Git workflow for merging changes into a repository. You'll go through the steps of forking a repository, cloning it, creating a new branch, making changes, and pushing those changes to the remote repository.

## Fork - clone - status

### Fork the following repository

Start by creating a copy of the repository under your GitHub account by "forking" it. Fork the following repository https://github.com/andreia-oca/git_good_workshop.

Forking allows you to work on your own version of the repository, ensuring that the original repository remains unaffected by your changes.

### Clone it on your local machine:
Once you've forked the repository, clone it to your local machine to start working on it:

```bash
git clone https://github.com/andreia-oca/git_good_workshop
```

This command copies the content of the repository to your computer, where you can modify and experiment without affecting the remote repository until you're ready to push changes.

### Check the status of the repository:
To verify your current working state, use the git status command:

```bash
$ git status
```

You terminal should look like this:

```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

The information provided by this is the following:
* On branch main: You are on the main branch (the default branch).
* Up to date with 'origin/main': Your local branch is synchronized with the remote main branch.
* Nothing to commit, working tree clean: No files have been changed or added to the staging area.

## Create a branch - make a change - commit - push

Now, let's go through the process of creating a new branch, making changes, committing those changes, and pushing them to the remote repository.

### Create a branch

Branching is a key aspect of Git. It allows you to create a separate workspace where you can make changes without affecting the main branch. Run the following command to create a new branch for your testimonial:

```bash
git checkout -b <name>-testimonial
```

Replace <name> with your actual name. For example, if your name is Alex, you'd run:
```bash
git checkout -b andreia-ocanoaia-testimonial
```

This command does two things:

* Creates a new branch called alex-testimonial.
* Switches to that new branch, allowing you to work on it.

You can run `git status` to verify that you are now on the new branch.

### Make a change

In the sections directory, create a new markdown file with your name. This file will contain your testimonial or expectations for this workshop. Name the file <name>.md (again, replacing <name> with your name), and add your text.

Check the status of the repository with `git status` to see the new file you've created. You'll see that the file is untracked.

Add it to the staging area with the following command:

```
git add sections/<name>.md
```

Check the status again to see that the file is now staged for commit.

### Commit your changes

You are now ready to commit your changes. Run the following command:
```
git commit -m "Add <name> testimonial"
```
Every commit should have a message that describes the changes made in that commit. This is useful as a piece of documentation near the codebase. Later on in the workshop, we'll see how to track changes and understand the history of a project using these commit messages.

You can check the status again to see that your file has been committed and the staging area is cleaned.

To inspect your commit again there are two commands:
```
# This command shows the commit history
git log
```

and
```
# This command shows the changes made in the last commit
git show
```

Push the change to the repository:

```
git push origin <name>-testimonial
```

Congratulations! You've successfully created a new branch, made changes, committed them, and pushed them to the remote repository. You can now open a pull request to merge your changes into the main branch.

## Remote repository - origin and upstream

In `git`, `origin` and `upstream` refer to different remote repositories used for collaboration and version control.
The `origin` refers to the repository you cloned from, while `upstream` refers to the original repository from which your repository was forked.

`origin` is the default name for the remote repository from which you cloned your project. It typically refers to your main remote repository, where you push your changes and pull updates.

You can verify the remote setup using:

```bash
git remote -v
```

Your terminal will print something like this:
```
origin  https://github.com/user/my-project.git (fetch)
origin  https://github.com/user/my-project.git (push)
```

If your repository is forked from another repository, you can set up the `upstream` remote to track the original repository. This allows you to pull changes from the original repository into your forked repository.

```
upstream  https://github.com/user/my-project.git (fetch)
upstream  https://github.com/user/my-project.git (push)
```

You would use upstream to pull changes from the main project (the original repository) into your local repository so that your fork stays up to date with the main one.
