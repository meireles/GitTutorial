# Grand Challenges for Great Minds
-

Our goal is that you lean the basics of git by using it, and that you end the class time with your group project versioned! We do not want to mess up your work though, so we'll use training wheels first.

#### We need your feedback!

* Start a task with your post-it notes down
* Having trouble? Put the **<span style="color:red">red post-it</span> up**
* Finished your task? Put the **<span style="color:green">green post-it</span> up**

#### Use the [cheat sheet](cheat_sheet.md)!

## Challenges

### On your own
You will work with a toy example.

1. [Create a repo](#create_repo) ~ 3 min
2. [Work, add, commit](#work_add_commit) ~ 7 min
3. [Commit cycle and Exploring versions](#explore) ~ 9 min
4. [Undoing things](#undo) ~ 7 min
5. [GitHub](#remote) ~ 10 min

### Team up
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
* Add a comment to the function **best_beer**
* What is the status of your git repo now?
* Find the what changed between your current **best_beer.R** and the previous version.
* Happy with your comment? Staging it!

### Task 2:
* Now change **best_beer** to reflect poor taste (replace "IPAs" with "Lager")
* What is the status of your repo?
* Suppose that you really love "Lagers". Commit our newest change (tricky)!
* Did it work? Find out which version has been committed.

##4. Undoing things <a id="undo"></a>