# Know your history - Create a `git hist` alias

In this challenge, your goal is to create a global git alias called `hist` that displays the commit hash, date, message, and author in a neat format, similar to:

When executing `git hist` the output should be similar:

```bash
* 5e2a9f1 Thu Sep 26 17:12:47 2024 +0300 | docs: update readme [Andreia Ocănoaia]
* 488878a Thu Sep 26 17:11:23 2024 +0300 | docs: add workshop mindset [Andreia Ocănoaia]
* a2f1a6b Thu Sep 26 17:10:46 2024 +0300 | docs: rename sections files [Andreia Ocănoaia]
```

You’ll need to configure this alias using  `git config` or by editing `~/.gitconfig`.

Instead of using the cluttered `git log`, you can now use your brand new `git hist` to check the older commits.

[Guidelines and docs](../sections/02-make-yourself-at-home.md)
