# Using GitHub

If cloned from a server, your repo should already have a connected remote (origin). To list the remotes connected to your repo, run:

```bash
git remote -v
```

If you started from scratch, first create a remote repo on github. To connect your local repo to the new remote repository, perform:

```bash
git remote add origin <url_remote_repo>
```

To push your local changes to the remote server, simply:

```bash
git push origin master
```

And to update you repo with the newest changes from origin (server), use:

```bash
git pull origin master
```
