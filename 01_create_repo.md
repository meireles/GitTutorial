#2. Creating a repository

First we'll need to create a new directory (using `mkdir`) and move into it (using `cd`). I named my directory `bogus`

    mkdir bogus
    cd bogus

Then we'll ask git to magically transform our boring directory into a repository!

    git init

This magic happens because git adds a hidden special sub-directory called `.git/`. If you don't belive me, list everything inside `bogus` and see for yourself.

     ls -a

Now git is keeping track of everything that happens inside that reposidory. It knows when you add / change or delete a file.

You can check on the status of your project with the command

    git status

And remember this one, you'll need it a lot. 


## Hands on

1. Create a new directory named **dumb**
2. Move into that dectory
3. Create a git repository
4. Check its status
5. remove the subsirectory `.git` using the command `rm -rf .git`
6. Check the status of your repository again


## Nested repos
Nothing stops you from creating a sub-directory in your repo and setting up another repo inside it. Is this a good idea? Why or why not?
