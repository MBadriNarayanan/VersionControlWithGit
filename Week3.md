### Week 3

#### Resolving Merge Conflicts

* Create a local repository "MergeConflict"
* Create a commit with Doc1.txt containing "feature 1" and commit message "add feature 1". Commit should be made on the master branch.
* Create and checkout a branch off of the latest master commit named "featureX"
* Create a commit on the featureX branch : 
  * modify Doc1.txt , adding "feature 2" directly under the line "feature 1"
  * add a commit message of "add feature feature 2"
* Checkout the master branch
* Create a commit on the master branch : 
  * modify Doc1.txt , adding "feature 3" directly under the line "feature 1"
  * add a commit message of "add feature feature 3"
* Verify that the master branch is checked out.
* Execute : git merge featureX and attempt to merge in the featureX branch. We would get a merge conflict.
* Execute : git status to see that Git has modified Doc1.txt .
* View the Doc1.txt file. Notice the conflict markers in the file. That is the part of the
merge that Git couldn't automatically resolve.
* To abort the merge process : git merge -- abort
* Verify that we are back to the state before the merge attempt, with no uncommitted files
in the working tree.
* Solving the merge conflict : Repeat the merge attempt. We should again
see a merge conflict.
* Edit Doc1.txt to resolve the merge conflict. Remove the conflict markers and make
sure the file contains three lines of text: "feature 1", "feature 2" and "feature 3".
* Add Doc1.txt to the staging area so that the fixed version of the file is part of the merge
commit.
* Commit the merge. Accept the default merge commit message.
* Delete the featureX branch label.
* Verify that we have a commit graph with a merge commit containing all three features.


#### [Remote Repository URL](https://bitbucket.org/MBadriNarayanan/branchtracking)
#### Tracking Branches

* Create a remote repository "BranchTracking" using bitbucket
* Use bitbucket to create first commit : 
  * Click Create a README.
  * Modify the text to contain only the line # Branch Tracking README # .
  * Click Commit. Change the commit message to add README.md . Click Commit to create the commit
* Clone the BranchTracking repository.
* Use git branch --all to view the local and tracking branch names.
* Use git log --all --oneline --graph to view the combined log of all local and tracking
branches.
  * View the branch labels on the commit
#### Creating a state with the local branch one ahead of the tracking
branch.

* Modify the local README.md. Append the line "Fun with tracking branches." to the file.
Add and commit the file with the commit message of "add fun line to README.md".
* View the commit graph, again using the --all option. We should see that the master
branch label is on the latest commit, but the origin/master and origin/HEAD labels
have stayed on the original commit.
* Execute git status . Notice the message says your branch is ahead of the tracking
branch by one commit. This means that you have made one commit locally that is not on
the remote repository.
* Execute git push to push the commit to the remote repository. Execute the git log
and git status commands again. We should now see the three branch labels on the
latest commit. The local and remote repositories are again synchronized.



### Notes

* The master label represents the tip of the local master branch.
* The origin/master label represents the tip of the tracking branch that tracks the master
branch on the remote repository.
* The origin/HEAD label represents the tip of the default branch on the remote repository.
The default branch on the remote repository is the master branch.
* If you make a commit to the local repository without pushing it to the remote repository, the
local branch becomes ahead of the tracking branch. The tracking branch only knows what the
remote repository knows.
