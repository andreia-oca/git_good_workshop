# Advanced settings

## Setting up an ssh key to authenticate with GitHub

When you're working with GitHub, you can use an SSH key to authenticate with the platform. This is a more secure and easy way to connect to GitHub than using your username and password. Here's how to set up an SSH key:

Follow this [GitHub tutorial to configure a ssh key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) on your machine and use it forever to authenticate with GitHub.

## Pre-commit hooks

Pre-commit hooks are scripts that run automatically before a commit is made. They can be used to enforce coding standards, run tests, or perform other checks to ensure code quality. Here's how to set up and use pre-commit hooks:

Navigate to Your Repository's Hooks Directory: Go to the `.git/hooks` directory in your repository:

```bash
cd your-repo/.git/hooks
```

Create the Pre-commit Hook: Create a new file named pre-commit (without any file extension):

```bash
touch pre-commit
```

Make the Hook Executable: Change the permissions to make the script executable:

```bash
chmod +x pre-commit
```

Edit the Pre-commit Hook: Open the pre-commit file in your favorite text editor and add the following example script, which runs a simple Bash command:

```bash
#!/bin/bash

# Example command: Check for untracked files
if [[ $(git ls-files --others --exclude-standard) ]]; then
    echo "Error: You have untracked files in your working directory."
    echo "Please add or ignore them before committing."
    exit 1
fi

# Run any other Bash command you want
# For example, checking if a specific file exists:
if [[ ! -f "important-file.txt" ]]; then
    echo "Error: important-file.txt is missing. Please add it before committing."
    exit 1
fi

# If everything is okay, exit with a success status
exit 0
```

Test Your Hook: Now, when you try to make a commit, the pre-commit hook will run. If there are untracked files or if important-file.txt is missing, the commit will be aborted, and you'll see the respective error message.

## Test around

1. Set up an SSH key: Follow the GitHub tutorial to configure an SSH key on your machine.
2. Create a pre-commit hook: Create a pre-commit hook that checks for untracked files or missing files before committing.
