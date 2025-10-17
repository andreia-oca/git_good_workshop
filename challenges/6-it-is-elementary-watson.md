# It is elementary, Watson - use git bissect to find the flag

Sometimes finding the commit that introduced a bug—or a hidden feature—can feel like detective work. In this challenge, you’ll use git bisect, Git’s binary search tool, to quickly locate the commit that added a file containing a CTF flag.

Clone the following repository:
```bash
git clone  https://github.com/andreia-oca/ggw-crime-scene
```

Explore the commits: The repository has multiple commits that progressively modify files. Your goal is to find the commit that added a file containing the CTF flag of the format `git_good{<flag>}`.

Use `git bissect` to identify the commit that contains the flag.

[Guidelines and docs](../sections/06-who-dafaq-wrote-this-oh-its-me.md)
