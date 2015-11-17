#3. Doing Work


## The work -> add -> commit cycle

One your repo is up and running (remember to check using `git status`) it is time to actually get our hands dirty.


### Work

While inside your repo, create a new file called `add_one.R`. Mine will look like this.
    
    add_one = function(x){ x + 2 }

This was the "do work" part! I can check the status of my repo again

     git status

and that should say something like
     
    On branch master

    Initial commit

    Untracked files:
      (use "git add <file>..." to include in what will be committed)

	add_one.R

    nothing added to commit but untracked files present (use "git add" to track)

### Add

Git just said that our file is not being tracked. To make git keep track of it we have to run `git add`

    git add add_one.R

Then when we run `git status` again we should see

    On branch master

    Initial commit

    Changes to be committed:
       (use "git rm --cached <file>..." to unstage)

	    new file:   add_one.R

### Commit

If you are ready to take a snapshot of your project, you can use `git commit`

    git commit -m "added function that adds one to number"

If you run `git status`, you should see that everything is up to date. 
    
    On branch master
    nothing to commit, working directory clean
    
To see the version 


![](assets/xkcd1296_git_commit.png)

