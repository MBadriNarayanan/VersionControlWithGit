### Week 2

* Create a FileB.txt file for the Week2 folder using echo with the content "Hi This is Version Control with Git"
* To find the SHA-1 Value of the contents of FileB use the command : git hash-object FileB.txt

#### Git References

* Go to the directory of the remote repository and create FileA.txt with its content "feature 1" using the echo command
* Add FileA.txt to remote repository using : git add
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


#### Merging Branches
