
Creating the change
===================

    $ git checkout -b my-feature

... modify code ....

    $ git add <filename> 
    $ git commit -m “my feature is this”

... or, if you're lazy ...

    $ git commit -a -m "my feature is this"

... then fetch changes from master since we branched, and re-apply ours on top...

    $ git fetch
    $ git rebase master
    
... Also fine to merge here instead of rebase (but rebasing is better because makes it easier for others!). Resolve conflicts (if any) and add them ... 

    $ git add <filename>
    $ git rebase --continue

... # push my branch back to the server

    $ git push origin my-feature 

If you want to use git workflow to do code reviews (and are using github), at this point you can create a pull request. Using a pull request, you assign your buddy the task of approving merging your changes (from your feature branch back into master or a release branch). To create the pull request, go to your project on github.com, click "pull requests," then create.


Other guy merges in the changes
===============================
(assuming no pull request)

    $ git fetch 

... list branches

    $ git branch -a

... bring a branch local

    $ git branch --track my-feature origin/my-feature
    $ git checkout master
    $ git merge my-feature

... resolve conflicts and look around ...

    $ git push

... delete branch (and remote branch) when done

    $ git branch -d my-feature 
    $ git push origin :my-feature 
    
If you used the github pull request workflow, at this point, the reviewer should delete the feature branch.

Other useful commands
=====================

To remove remote branches from your list after they have been deleted by other people

    $ git remote prune origin
