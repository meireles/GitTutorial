#Exploring versions

To view you repo's history, such as what the commits were, who commited and when, use:

```bash
git log                      # See commit history
git log --author=coleoguy    # Only commits by coleoguy
git log --oneline            # Compact display of commit history
```

The crazy strings of characters that you see (like `9b79fbd948d5de3f30cdc...` are the commit's fingerprints (hash). You can always refer to a commit using that, or its first 5 characters `9b79f`. `HEAD` points to the most recent end of a commit chain, so we can refer to older commits using `HEAD~1` (previous), `HEAD~2` (two commits ago), and so on.


To see the difference between versions, run:

```bash
git diff                # working dir VS. (staged + commited)
git diff --staged       # staged VS. commited
git diff HEAD~1 <file>  # working dir VS. previous version
```

To make your working directory match how the **whole** repo was like in a previous version. 

```bash
git checkout <commit_id>
```

You can run the older analysis on your previous versin of the data.
You will see a scary 'detached HEAD' message. This means that nothing that you do will be saved (you can't commit, etc).

To _"go back"_ to your most recent version, simply:

```bash
git checkout master       # `go back` to most recent commit
```
