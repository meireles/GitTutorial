# Git cheat sheet


## Installing Git

* [Linux](http://git-scm.com/download/linux)
* [OSX](http://git-scm.com/download/mac)
* [Windows](https://git-for-windows.github.io)


## Table of Contents

### Preliminary

1. [How to type commands](#type_commands)
2. [The shell (or terminal, or gitBASH)](#the_shell)
3. [Configuring git](#config)

### Git

1. [Creating a repo](#create_repo)
2. [Doing Work, adding and committing](#work_add_commit)
3. [Exploring versions](#explore)
4. [Undoing Things](#undo)
5. [Syncing to a Server](#remote)
6. [Collaborating](#collaborate)
7. [Resources](#resources)


## How to type commands <a id="type_commands"></a>

When entering commands, you will always replace the text inside `{}` with your own information **and** get rid of the curly braces. For instance:

```bash
# If you want to create a directory named beer and you see:
mkdir {new_dir_name}
# You would actually type
mkdir beer

# If wanted to add my name to git configuration and I saw:
git config --global user.name "{your_name}"
# I would actually type
git config --global user.name "dudu meireles"  # Keeping quotes
```

## The shell (or terminal, or gitBASH) <a id="the_shell"></a>

### Basic shell commands

```bash
ls              # lists what is under your current directory
cd              # Changes directories
cd {go_here}    # To go to dir {go_here}
cd ..           # To go back (one dir up)

mkdir {new_dir} # makes a new directory
```

## Configuring git <a id="config"></a>

Tell git your name, email and that you'd like colored output.

```bash
git config --global user.name "{your_name}"
git config --global user.email "{your_email}"
git config --global color.ui true
```

## 1. Creating a repo <a id="create_repo"></a>

### 1.1. New repo from scratch

Inside a new directory, simply run:

```bash
git init
```

to create a repository. You can always create a new directory and then move into it using

```bash
mkdir {your_dir_name}     # makes a new dir
cd {your_dir_name}        # moves into a dir
```


### 1.2. Clone an existing Repo

You can copy (clone) and existing local repo

```bash
git clone {name_original_repo} {name_new_repo}
```

Or clone a repo from a remote server (such as github or bitbucket)

```bash
git clone {url_for_remote_repo} {new_repo_name}
```

For example:

```bash
git clone https://github.com/meireles/GitTutorial.git
```

## 2. Work, add and commit <a id="work_add_commit"></a>

After doing work, like creating or modifying things, you should check the status of your repo. This will tell you if files are not being tracked or have been modified.

```bash
git status
```

Now, there are two basic steps involved in versioning your work

### First: `add`

`add` tells git what change you want in the next snapshot. It places the file in the _staging area_.

```bash
git add {file_name}   # stages a specific file (file_name)
git add .             # stages all files
```

### Second: `commit`

`commit` actually saves a new version of your project, i.e. **it takes a snapshot**. Changes that were not added (not in the staging area) **will not** be saved in your commit.

```bash
git commit -m "{My short but descriptive commit message}"
```

####Remember:
You do not have to commit every single little change, because you don't need to take one full snapshot of your project all the time. Your working directory and staging area are your firends!

##3. Exploring versions<a id="explore"></a>

### 3.1. Repo History
To view you repo's history, such as what the commits were, who committed and when, use:

```bash
git log                        # See commit history
git log --author={author_name} # Only commits by authorname
git log --oneline              # Compact display of commit history
```
#### Crazy strings (like `9b79fbd948d5de3f30cdc...`)?
Relaxx, they are just the commit's fingerprints (hash). You can always refer to a commit using that, or its first 5 characters, for instance: `9b79f`.

`HEAD` points to the most recent end of a commit chain, so we can refer to older commits using `HEAD~1` (previous), `HEAD~2` (two commits ago), and so on.

### 3.2. What is different in an older file?

To see the difference between versions, run:

```bash
git diff                # working dir VS. (staged + committed)
git diff --staged       # staged VS. committed
git diff HEAD~1 {file}  # working dir VS. previous version
```

### 3.3. Back to the past & Back to the future

To make your working directory match how the **whole** repo was like in a previous version. 

```bash
git checkout {commit_id}   # commit_id is that crazy string
```

You can look around, run older analysis on your previous version of the data, etc. You will see a scary "detached HEAD" message. This means that __nothing that you do will be saved__ (you can't commit, etc).

To _"go back"_ to your most recent version, simply:

```bash
git checkout master       # `go back` to most recent commit
```

##4. Undoing Things <a id="undo"></a>

### 4.1. Undoing a specific change

If you changed a file (in your working directory) and want to discard those changes in favor of the previous version.

```bash
git checkout -- {filename}         # Get the previous {filename}
git checkout {commit} {filename}   # Get {filename} from a given {commit}
git checkout HEAD {filename}       # Get your most recent change back
```

#### Important:

When you use `git checkout {file}`, i.e. specifying a file to retrieve, __you will change the state of your repo!__

Thus, remember that `git checkout` can be a __read-only__ (as seen in 3.3) or __read-write__ operation (like here) depending on how you call it.

### 4.2. Undo all changes introduced by a commit

To revert all the changes that you made in a commit `{commit}`, run:

```bash
git revert {commit_id}     # Undo all changes introduced in <commit>
```

So if I want to undo the changes introduced in the last commit, I'll do:

```bash
git revert HEAD  # remember that HEAD points to my last commit
```

#### Important:
This command is not intuitive. It reverts (**undoes**) the changes introduced in `{commit}`. It **does not** revert **to** that commit. For example, if I do `git revert {commit3}` my history will look like this:

```bash
(commit1)----(commit2)----(commit3)----(commit4)
                             ^              ^
                             |              |
                         Undid this    Added new commit
                                       based on commit2
```

##5. "Syncing" to a Remote (e.g. Github)<a id="remote"></a>

If cloned from a remote repository, your repo should already have a connected remote (origin). To list the remotes connected to your repo, run:

```bash
git remote -v
```

If you see a list of urls, then you are all set.


### 5.1. Connect your repo to a remote
If you started a repo from scratch, first create a remote repo on github. You should get the address of your repo, which will look like:

```bash
https://github.com/meireles/GitTutorial.git
```
But will have your Github username instead of `meireles` and the name of your repo instead of `GitTutorial.git `.

To connect your local repo to the new remote repository, perform:

```bash
git remote add origin {url_remote_repo}
```

Make sure that you use the `https` address, since it requires less setup. Remember that `origin` will be the nickname of the remote repo in your local system. It is a very standard nickname and you should stick with it.

#### Send changes to the remote: `push`

To `push` (upload) your local changes to the remote server, enter:

```bash
git push origin master
```

#### Grab the updates from the remote: `pull`

And to update you repo with the newest changes from origin (server), use:

```bash
git pull origin master
```

##6. Collaborating <a id="collaborate"></a>

### 6.1. Workflow

An easy way to collaborate in git is to use a centralized workflow.

1. Collaborators clone your repo (see 1.2 to see how to clone)
2. You all begin a cycle of
   3. Getting other people's updates: `git pull origin master`
   4. Going through a **work -> add -> commit** cycle
   5. Sharing your changes: `git push origin remote`

### 6.2. Conflicts

Because your team is working in parallel, people may end up changing the same line on the same file. So when you try to:

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

Just edit the file picking the correct line (`Who is taller: Heath` in this case), and get rid of the `<<<<<<< HEAD`, `=======` and `>>>>>>>`.

Now you can:

```bash
git add bs.txt
git commit -m "{Merge changes from GitHub}"
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
