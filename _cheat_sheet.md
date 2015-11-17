# Git cheat sheet


## Installing Git

* [Linux](http://git-scm.com/download/linux)
* [OSX](http://git-scm.com/download/mac)
* [Windows](https://git-for-windows.github.io)


## Table of Contents

1. [Creating a repo](#create_repo)
2. [Doing Work, adding and commiting](#work_add_commit)
3. [Exploring versions](#explore)
4. [Undoing Things](#undo)
5. [Syncing to a Server](#remote)
6. [Collaborating](#collaborate)


## 1. Creating a repo <a id="create_repo"></a>

### New repo from scratch
Create a new directory (using `mkdir`), move into it (using `cd`) and execute:

```bash
git init
```

### Clone an existing Repo

You can copy (clone) and existing local repo

```bash
git clone <path_to_repo> <new_repo_name>
```

Or clone a repo from a remote server (such as github or bitbucket)

```bash
git clone <url_for_remote_repo> <new_repo_name>
```

## 2. Work, add and commit <a id="work_add_commit"></a>

After doing work, like creating or modifying things, you should check the status of your repo. This will tell you if files are not being tracked or have been modified.

```bash
git status
```

Now, there are two basic steps involved in versioning your work

**1st.** `add`: Tells git what change you'll want in the next project snapshot. (Indexes a file in the staging area).

```bash
git add <filename>
git add *            # adds all files
```

**2nd.** `commit`: This actually saves a new version of your project, i.e. takes a snapshot. Changes that were not added (not in the staging area) __will not__ be saved in your commit.

```bash
git commit -m "My short but descriptive commit message"
```

##3. Exploring versions<a id="explore"></a>

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

##4. Undoing Things <a id="undo"></a>

###TODO!
```bash
git checkout -- <filename>
git checkout <commit> <filename>   # Get the file <filename> from <commit>
```

```bash
git revert
```


##5. "Syncing" to a Server <a id="remote"></a>

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

##6. Collaborating <a id="collaborate"></a>

An easy way to collaborate in git is to can use a centralized workflow.

1. Colaborators clone your repo
2. You all begin a cycle of
   3. Geting other people's updates: `git pull origin master`
   4. Going through a **work -> add _ commit** cycle
   5. Sharing your changes: `git push origin remote`


Because your team is workig in parallel, people may end up changing the same line on the same file. So when you try to

```bash
git pull origin master
```
 
You will end up with a conflict:

```
CONFLICT (content): Merge conflict in bs.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Conflicts aren't bad though. All you have to do is open the file that has the conflict (`bs.txt` in our example) and choose which change is correct. The conflicting parts of the file show up between `<<<<<<< ` and `>>>>>>> `, like in the example below.

```
<<<<<<< HEAD
Who is taller: Dudu
=======
Who is taller: Heath
>>>>>>> 
```

Just pick the correct line (`Who is taller: Heath` in this case), and get rid of the `<<<<<<< HEAD`, `=======` and `>>>>>>>`.

Now you can:

```bash
git add bs.txt
git commit -m "Merge changes from GitHub"
git push origin master
```

