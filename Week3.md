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
  
  
#### Creating a state with the local branch one ahead of the tracking branch

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



#### [Remote Repository URL](https://bitbucket.org/MBadriNarayanan/fetchpullpush)

#### Fetch,Push,Pull

* Create a remote repository "FetchPullPush" using bitbucket
* Use bitbucket to create first commit : 
  * Click Create a README.
  * Modify the text to contain only the line # Fetch Pull Push README # .
  * Click Commit. Change the commit message to add README.md . Click Commit to create the commit
* Clone the Fetch Pull Push repository.
* Using Bitbucket, modify and commit the README.md file.
  * Click on the Source tab.
  * Click on README.md.
  * Click Edit.
  * Append the line "Network Line Commands"
  * Click Commit and specify a commit message "Added Network Line Commands".
* Because we have created a commit on the remote repository after cloning the repository,
your local master branch is behind. View your commit history. Git is not aware of the new
remote commit, because you have not executed any network commands like git fetch .
* Execute : git fetch 
* View the commit graph. We should see your second commit, and
that the tracking branch is ahead of your master branch.
* We would have fetched the latest commits from the remote repository.


#### Execute a pull with a fast-forward merge.

* Because we have not added any commits to our local master branch, we can perform a
pull with a fast-forward merge.
* Execute : git pull . Because this merge is fastforwardable, no merge commit will be created.
* View the commit graph. The 'master' branch label should move to the latest commit.
The master branch is synchronized.


#### Execute a pull with a merge commit.
* In your local repository, create an empty Doc1.txt file. Add and commit the file,
specifying a commit message of "Added Doc1.txt". Do not Push the commit.
* In Bitbucket, make a minor edit to the README.md file. Commit the change.
* In the command line, execute : git fetch 
* We should now see that your local master branch is 1 ahead and 1 behind the tracking branch. This is because you made commits
locally and in the remote repository.
* Attempt a git push 
* We will receive a message saying that the updates were rejected,
because the tip of your current branch is behind the tracking branch. The message
suggests to do a pull.
* Execute : git pull . Notice that a merge commit was created, combining the work of your
local commit and the commit that you made on the remote repository. Also notice that the
tracking branch is now two commits behind. 
* At this point, the remote repository doesn't
know about your Doc1.txt commit or about the local merge commit.

#### Push commits to the remote repository.

* Execute : git push to add the two local commits to the remote repository. We should
now see that the local and tracking branches are synchronized.
* In Bitbucket, click on Commits and verify that the commit graph matches your local
commit graph.




#### Rebase

* Create a local repository named "Rebase" 
* Create an initial commit that adds an empty FileA.txt file. The commit message should be "add fileA.txt".
* Create a feature1 branch.
* Create a commit on the feature1 branch. Add the string "feature 1 wip" to fileA.txt . The commit message should be "add feature 1 wip".
* Checkout the master branch. Create a commit that adds an empty fileB.txt file. The commit message should be "add fileB.txt".
* View your commit graph and notice that it is no longer linear. Be sure to use the --all
option with git log . (Use the command git log --all --graph --oneline)
* Rebase the commit on the feature1 branch to the tip of the master branch . Do this by
first checking out the feature1 branch. 
* Execute : git rebase master.
* View the commit graph. It should now be linear. Verify that you can see fileB.txt in
your working tree of feature1.

#### Rebase and resolving a merge conflict

* Checkout the master branch.
* Create a commit on the master branch. Add the string "feature 2" to fileA.txt . The
commit message should be "add feature 2".
* Rebase the feature1 branch onto the tip of the master branch. This will involve
resolving a merge conflict, because the master branch and the feature1 branch both
modified the same part of fileA.txt in different ways.
* Checkout the feature1 branch.
* Execute : git rebase master . Notice that there are merge conflicts.
* Execute : git status to view the status of the rebase.
* Fix the content of fileA.txt so that "feature 1 wip" is before "feature 2".
* Stage the fixed file.
* Execute : git rebase --continue .
* View the commit graph. 
* Verify we get a linear graph

#### Rewriting a Commit History

* Create a local repository "ChangeCommit"
* Create an initial commit that adds a fileA.txt file containing the text "mistake". The
commit message should be "add fileA.txt with mistake". Note the first to characters of the
commit's SHA-1.
* Amend the previous commit by executing git commit --amend -m "add fileA.txt" .
  * Modify fileA.txt so that it is empty.
  * Add fileA.txt to the staging area.
  * Amend the previous commit by executing git commit --amend -m "add fileA.txt" .
* Notice the SHA-1 of your amended commit. It should be different than the one you noted
prior to amending the commit.

#### Use interactive rebase to remove a commit.

* Create a feature1 branch.
* Create a commit on the feature1 branch. Add the string "feature 1 wip" to fileA.txt .
* The commit message should be "add feature 1 wip".
* Create another commit on the feature1 branch. The contents of fileA.txt should be
"feature 1". The commit message should be "add feature 1".
* Let's say that you think that the "feature 1 wip" commit adds little value to the commit
history. Use interactive rebase to remove that commit by squashing it.
  * Checkout the feature1 branch.
  * View the commit graph of the feature1 branch.
  * Execute git rebase -i <SHA-1> , where is for the initial commit of the repository (which is also the first commit of the feature1 branch).
  * Explore the interactive rebase editor.
  * Remove the commit with the commit message of "feature 1 wip". Do this by changing the pick command to squash for the commit with a commit message of "add feature 1". Save the file.
  * An editor then opens for the commit message of the squashed commit. Change it to
simply read add feature 1 .
  * View your commit graph. Verify that the commit with a message of "feature 1 wip" has been removed.
  * Merge the feature1 branch and delete its branch label.


#### Perform a squash merge.

* Create a feature2 branch off of the master branch.
* Create a commit on the feature2 branch. Add the string "feature 2 wip" to fileA.txt .
* The commit message should be "add feature 2 wip".
* Create another commit on the feature2 branch. In fileA.txt , change the line "feature 2 wip" to "feature 2". The commit message should be "add feature 2".
* Perform a squash merge of the feature2 branch into the master branch.
* Checkout the master branch.
* Execute : git merge --squash feature2 .
* Execute : git commit . An editor opens. Specify a commit message of "add feature 2".
* View the commit graph. Notice that the commit with a message of "feature 2 wip" is not
part of the master branch.
* Delete the feature2 branch label. This will create two "dangling" commits that will be
garbage collected.

