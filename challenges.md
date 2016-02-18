# Grand Challenges for Great Minds
--

Our goal is that you lean the basics of git by using it, and that you end the class time with your group project versioned! We do not want to mess up your work though, so we'll use training wheels first.

#### Use the [cheat sheet](cheat_sheet.md)!

Remember that you will do the vast majority of your work from the command line (shell). Windows users will work from the __gitBash__ program.

## Challenges

### On your own
You will work with a toy example.

1. [Create a repo](#create_repo) ~ 3 min
2. [Work, add, commit](#work_add_commit) ~ 7 min
3. [Commit cycle and Exploring versions](#explore) ~ 10 min
4. [Undoing things](#undo) ~ 10 min
5. [GitHub](#remote) ~ 10 min

### Teamed up
1. Demo ~ 5 min
2. [Collaborating](#collaborate)

##1. Create a repo <a id="create_repo"></a>

### Task:
* Create a repo from scratch named **beer**
* Check the status of your repo
* Find the subfolder where the git magic happens (its hidden)

#### Hints: 
Shell Commands: The `mkdir <dir_name>` creates a new directory. Use the `cd <dir_name>` command to move into a dir. The command `ls` lists the files in a directory and `ls -a` lists the hidden files too.


##2. Work, add, commit <a id="work_add_commit"></a>

### Task:
* Create a file called **best_beer.R** that has a function like

```r
best_beer <- function(){print("I love IPAs")}
```

* What is the status of your git repo?
* Add your changes to the staging area
* What's the status now?
* Commit your changes
* Did your commit work? How can you get your repo's history?

##3. Commit cycle and Exploring versions <a id="work_add_commit"></a>

### Task 1:
* Add a comment on top of the function **best_beer**
* What is the status of your git repo now?
* Find the what changed between your current **best_beer.R** and the previous version.
* Happy with your comment? Stage it!


### Task 2:
* Now change **best_beer** to reflect poor taste (replace "IPAs" with "lagers")
* What is the status of your repo? Pay close attention!
* Suppose that you really love lagers. Commit our newest change (tricky)!
* Did it work? Find out which version has been committed.

##4. Undoing things <a id="undo"></a>

### Task 1:
* Make sure that your repo is clean (everything is committed)
* Open **best_beer** and replace "love" with "hate"
* Oops, you didn't really mean that. Tell git that you want to discard (undo) that last change in **best_beer.R**.
* Guess what the status of you repo is. Now check; did you get it right?

### Task 2:
You wake up the next day with a big headache, and your R function is broken, since it prints `"I love lagers"`.

* Undo the whole last commit
* Did it work? What is the status?
* Did you end up erasing the "broken commit" from history?

##5. GitHub <a id="remote"></a>

### Task:

* Create a remote **beer** repo on github
* Connect your local repo to your brand new remote github repo
* Did it work? List the remote repos connected to your local machine
* Push your local repo to your remote
* Go to the Github webpage and confirm that your stuff is there

--
# Collaborate on your projects <a id="collaborate"></a>
--

* Team up in your groups
* Choose who will own the remote repository

* **Owner**
 * Create a git repo in your project's dir (locally)
 * add and commit your files
 * Create a remote repo on GitHub
 * Push your local repo to the remote

* **Collaborators**
 * Clone the owner's repo from github to your computer
 * Change something (even trivial, like adding a comment)
 * Commit your changes
 * Update from remote (someone might have already added stuff)
 * Check the status of your repo
 * Upload your changes to GitHub
