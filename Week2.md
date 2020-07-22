### Week 2

#### Git IDs

* Create a FileB.txt file for the Week2 folder using echo with the content "Hi This is Version Control with Git"
* To find the SHA-1 Value of the contents of FileB use the command : git hash-object FileB.txt

#### Git References

* Go to the directory of the remote repository and create FileA.txt with its content "feature 1" using the echo command
* Add fileA.txt to remote repository using : git add
* Commit using : git commit -m "Added Feature 1.txt"
* Push using : git push origin master
* Check log using : git log --oneline
* Execute : git show command
  * git show (first four characters of SHA-1)
  * git show (complete SHA-1)
  * git show HEAD
  * git show master
* If there exists multiple commits execute : git show HEAD~ to view the details of the parent
of the latest commit. Execute git show HEAD^ to see the same details. ~2, ~~ or ^^ refer to the grandparent. ^2 refers to the second parent in a merge commit.

#### Tag the commit

* At the location of the remote repository, execute the command : git tag to view existing  tags
* Execute : git tag -a -m "includes feature 1" v0.1
* Execute the command : git tag to view the created tag
* Execute : git show v0.1. We will be able to see tag information, as well as information on its associated commit object.
* Push tag to remote repository using : git push origin v0.1
* If there are multiple commits, tag the parent of the current commit with a "temp" tag. Wecan use the HEAD~ reference to refer to this commit, by executing the command: git tag -a -m "just a temp tag" temp HEAD~
* Delete tag using : git tag -d temp

#### Git Branches

* Create a local repository Branching
* Create a commit with FileA.txt containing "feature 1" and commit message "add feature 1". Commit should be made on the master branch.
* Verify only one branch exists and its name is master by using : git branch
* git log --oneline --graph command is used to check if we are on the most recent commit
* Create a branch featureX using any method
  * Method 1 : 
              * Command 1 : git branch featureX
              * Command 2 : git checkout featureX

  * Method 2 : git checkout -b featureX
  
 * Execute : git branch to verify if branch featureX has been created and it is the currently checked out branch
 * Execute : git log --oneline --graph to verify that thefeatureX branch is the current branch
 
#### Creating commits on the branch

* Create a commit on the featureX branch : 
  * modify fileA.txt , adding "feature mistake" directly under the line "feature 1" 
  * add a commit message of "add feature mistake"
* Execute : git log --oneline --graph --all to view the commit graph. 
* Execute : git checkout master to checkout the master branch. The working tree will be
updated with the older version of fileA.txt . View the contents of that file and verify that
you do not see your "feature mistake" content. The master branch is unaware of the work
that you did on the featureX branch.
* Execute git log --oneline --graph . Notice that only information about the current
branch is listed. Also notice that the current branch is the master branch HEAD ->
master . If you changed the working tree and committed right now, the commit would be
to the master branch.
* Execute git log --oneline --graph --all . Add --all shows all of the local branches.
Now you can see your featureX branch, and the featureX branch has a commit more
current than the commit at the tip of the master branch. We would see a straight line, with two commits on the featureX branch.
* Change back to the featureX branch by executing : git checkout featureX
* Create a commit on the featureX branch : 
  * modify fileA.txt , under "feature 1", change the line "feature mistake" to "feature
bigger mistake"
  * add a commit message of "add feature bigger mistake"
* Execute git log --oneline --graph --all and view the commit graph. We should again see a straight line, with two commits on the featureX branch.
* To view the first change that we made on the featureX branch. Execute :  git checkout HEAD~
* Verify that we are seeing the older version of fileA.txt ("feature mistake") in our working tree. Execute : git log --oneline --graph --all and notice that the current commit has a HEAD tag with no branch label. We will be in detached HEAD State.
* Checkout the master branch to get out of the detached HEAD state.

#### Deleting A Branch

* To delete the featureX branch use : git branch -d featureX . We will see that Git
won't let you delete this branch, because it has not been merged. The two commits on
the featureX branch would become "dangling commits" and would eventually be
garbage-collected by Git. In the Git message, notice that it says that if you are sure that
you want to delete the branch, use the -D option with the git branch command.
* Delete the featureX branch again using : git branch -d featureX
* View the commit graph and verify that you are back to having only a master branch by using the command : git log --oneline
* To undo the delete execute :  git reflog 
  * This shows the local history of HEAD references. Since Git doesn't immediately
delete commits, you can find the SHA-1 of your most recent featureX branch there.
  * Copy the SHA-1 of the "add feature bigger mistake" commit. 
  * Execute git checkout -b featureX [SHA-1 YOU COPIED] . 
* View the commit graph and verify that featureX branch has returned.
* Delete the featureX branch again.


#### Merging Branches
