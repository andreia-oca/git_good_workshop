# Repair your mistakes - `git rebase -i`

Not all commit histories are clean — sometimes, messy sequences of “fix typo”, “oops”, or “final version” commits can make the log hard to follow.Interactive rebasing allows you to rewrite and clean up commit history before sharing it with others.

Clone the following repository:
```bash
git clone  https://github.com/andreia-oca/ggw-cluttered
```

Check the older commits - it's madness there - somebody should clean that up.

Use `git rebase -i` to have the following history only:

```
* 5e2a9f1 Thu Sep 26 17:12:47 2024 +0300 | commit 03: update documentation
* 488878a Thu Sep 26 17:11:23 2024 +0300 | commit 02: add source code
* a2f1a6b Thu Sep 26 17:10:46 2024 +0300 | commit 01: initial commit
```

You’ll need to reorder, squash, and edit commit messages during the rebase to achieve this clean structure. When done, check the log to confirm the history matches the desired format.

[Guidelines and docs](../sections/05-code-review-shenanigans.md)
