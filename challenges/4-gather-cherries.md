# Gather cherries - Use `cherry-pick` to bring it all together

Sometimes useful work is scattered across different branches, and instead of merging everything, you just want to pick specific commits and apply them directly onto another branch. That’s where git cherry-pick comes in handy.

Clone the following repository:
```bash
git clone  https://github.com/andreia-oca/ggw-lost-cherries.git
```

Explore the branches `living_room`, `basement`, `terrace` and the commits ahead of main.

Each branch contains a few commits that are ahead of main. Your task is to bring all those changes together by cherry-picking the commits onto the main branch — without merging the branches themselves.

[Guidelines and docs](../sections/04-hot-fixing-in-production.md)
