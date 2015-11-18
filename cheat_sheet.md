# Git cheat sheet


## Installing Git

* [Linux](http://git-scm.com/download/linux)
* [OSX](http://git-scm.com/download/mac)
* [Windows](https://git-for-windows.github.io)


## Table of Contents

1. [Creating a repo](#create_repo)
2. [Doing Work, adding and committing](#work_add_commit)
3. [Exploring versions](#explore)
4. [Undoing Things](#undo)
5. [Syncing to a Server](#remote)
6. [Collaborating](#collaborate)
7. [Resources](#resources)


## Configuring git <a id="config"></a>

Tell git your name, email and that you'd like colored output.

```bash
git config --global user.name "YOUR_NAME"
git config --global user.email "YOUR_EMAIL"
git config --global color.ui true
```

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

For example: `git clone https://github.com/meireles/GitTutorial.git`

## 2. Work, add and commit <a id="work_add_commit"></a>

After doing work, like creating or modifying things, you should check the status of your repo. This will tell you if files are not being tracked or have been modified.

```bash
git status
```

Now, there are two basic steps involved in versioning your work

**First.** `add`: Tells git what change you want in the next snapshot. It places the file in the _staging area_.

```bash
git add <filename>   # stages a specific file
git add *            # adds all files
```

**Second.** `commit`: This actually saves a new version of your project, i.e. takes a snapshot. Changes that were not added (not in the staging area) __will not__ be saved in your commit.

```bash
git commit -m "My short but descriptive commit message"
```

Remember: You do not have to commit every single little change. Your working directory and staging area are your firends!

##3. Exploring versions<a id="explore"></a>

### Repo History
To view you repo's history, such as what the commits were, who committed and when, use:

```bash
git log                       # See commit history
git log --author=<authorname> # Only commits by authorname
git log --oneline             # Compact display of commit history
```

The crazy strings of characters that you see (like `9b79fbd948d5de3f30cdc...` are the commit's fingerprints (hash). You can always refer to a commit using that, or its first 5 characters `9b79f`. `HEAD` points to the most recent end of a commit chain, so we can refer to older commits using `HEAD~1` (previous), `HEAD~2` (two commits ago), and so on.


### What is different in an older file?

To see the difference between versions, run:

```bash
git diff                # working dir VS. (staged + committed)
git diff --staged       # staged VS. committed
git diff HEAD~1 <file>  # working dir VS. previous version
```

### Back to the past & Back to the future

To make your working directory match how the **whole** repo was like in a previous version. 

```bash
git checkout <commit_id>
```

You can look around, run older analysis on your previous version of the data, etc. You will see a scary 'detached HEAD' message. This means that __nothing that you do will be saved__ (you can't commit, etc).

To _"go back"_ to your most recent version, simply:

```bash
git checkout master       # `go back` to most recent commit
```

##4. Undoing Things <a id="undo"></a>

### Undoing a specific change

If you changed a file (in your working directory) and want to discard those changes in favor of the previous version.

```bash
git checkout -- <filename>         # Get the previous <filename>
git checkout <commit> <filename>   # Get <filename> from <commit>
git checkout HEAD <filename>       # Get your most recent change back
```

Note that when you use `git checkout <file>` specifying a file to retrieve, you will change the state of your repo! Thus, remember that `git checkout` can be a __read-only__ or __read-write__ operation depending on how you call it.

### Undo all changes introduced in the last commit

To revert all the changes that you did in your last commit <commit>, run 

```bash
git revert <commit>     # Undo all changes introduced in <commit>
```

##5. "Syncing" to a Server <a id="remote"></a>

If cloned from a server, your repo should already have a connected remote (origin). To list the remotes connected to your repo, run:

```bash
git remote -v
```

#### Connect your repo to a remote
If you started from scratch, first create a remote repo on github. To connect your local repo to the new remote repository, perform:

```bash
git remote add origin <url_remote_repo>
```
Make sure that you use the `https` address, since it requires less setup. Remember that `origin` will be the nickname of the remote repo in your local system. It is a very standard nickname and you should stick with it.

#### Send changes to the remote: `push`

To push your local changes to the remote server, simply:

```bash
git push origin master
```

#### Grab the updates from the remote: `pull`

And to update you repo with the newest changes from origin (server), use:

```bash
git pull origin master
```

##6. Collaborating <a id="collaborate"></a>

An easy way to collaborate in git is to can use a centralized workflow.

1. Collaborators clone your repo
2. You all begin a cycle of
   3. Getting other people's updates: `git pull origin master`
   4. Going through a **work -> add -> commit** cycle
   5. Sharing your changes: `git push origin remote`


#### Conflicts

Because your team is working in parallel, people may end up changing the same line on the same file. So when you try to

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

##7. Resources <a id="resources"></a>

### GUIs for Git
* [Sourcetree](https://www.sourcetreeapp.com)
* [GitHub Desktop](https://desktop.github.com)

### Visual Diff & Merge
* [Meld](http://meldmerge.org)

### Tutorials
* [Atalassian (BitBucket)](https://www.atlassian.com/git/tutorials)
* [GitHub -- Try Git](https://try.github.io/levels/1/challenges/1)
* [Branching Demo](http://pcottle.github.io/learnGitBranching/?NODEMO) -- really awesome


