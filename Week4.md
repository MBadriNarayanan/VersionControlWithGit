### Week 4

#### Single Repository Pull Request

* Create a remote repository "PullRequest1" in bitbucket
* Create and commit a README.md file containing the text # Pull Request 1 # with a commit message of "Initial Commit"
* Clone the repository locally
* Create a branch named "feature1" off of the master branch. This will be the
branch that is part of the single repository pull request.
* Create a commit on the feature1 branch containing a file named fileA.txt with the line "feature 1"
as the content of the file.
* Push the feature1 branch to the remote PullRequest1 repository using : git push --set-upstream origin feature1

#### [Remote Repository URL](https://bitbucket.org/MBadriNarayanan/pullrequest1)

#### Create a Pull Request

* In Bitbucket, navigate to the PullRequest1 repository. Click on Pull requests . Click on Create pull
request .
* In the Create a pull request window, select the feature1 branch on the left and the master
branch on the right. Modify the information if you would like and select Create pull request . You
should see that your pull request was created.

#### Merging a Pull Request

* In Bitbucket, navigate to the PullRequest1 repository. Click on Pull requests . You should
see your pull request. Click on the link to view the pull request.
* Click the Merge button associated with your pull request. Accept the default commit message and merge
strategy (merge commit). Click Merge . You should see that the feature1 branch is now merged. Click
on Commits and verify that the work of feature 1 is now in your commit graph.
* In the command line, execute a pull to add the new merge commit to your local repository.
* Delete the feature1 branch label locally and on origin . 
  * To delete the branch label locally execute : git branch -d feature1
  * To delete the origin (remote) branch, view the project in Bitbucket. Select Branches , then All branches . Click the ... next to the branch name, then Delete .

  
#### Fork A Remote Repository

* Create a remote repository "PullRequest2" in bitbucket
* Create and commit a README.md file containing the text # Pull Request 2 # with a commit message of "Initial Commit"
* Fork the PullRequest2 Repository

#### Synchronizing a forked repository using Bitbucket

* In the upstream repository PullRequest2 , update README.md and create a commit. You can do this
directly in Bitbucket or from your local client, pushing the changes to PullRequest2 .
* In Bitbucket, navigate to PullRequest2Fork .
* Select the Source tab. View the Repository details in the upper right. You may need to click on the icon in
the upper right (or press ]) to expand the repository details, then click > to show the dropdown.
* Click the Sync (1 commit behind) link. Accept the default merge message and click Sync .
* Click the Commits link. Notice that a merge commit was created in your fork.

#### Create a Multi Repository Pull Request

* Clone PullRequest2Fork to create a local repository for the forked repository.
* Create a branch named feature1 off of the master branch. This will be the branch that is part of the
pull request.
* Create a commit on the feature1 branch containing a file named fileA.txt with the line "feature 1"
as the content of the file.
* Push the feature1 branch to the remote PullRequest2Fork repository using git push --set-upstream origin feature1
* In Bitbucket, navigate to the PullRequest2Fork repository. Click on Commits and Branches to verify that
your feature1 branch and commit are on the remote repository.
* Click on Pull requests . Click Create pull request .
* On the Create a pull request page, select feature1 on the left and master on the right. Modify
the information if you would like and select Create pull request . You should see that your pull
request was created.


#### Merge a multi repository pull request

* In Bitbucket, navigate to PullRequest2. This is the upstream repository. Click on Pull requests . You
should see the pull request from your fork.
* Click on the link to view the pull request.
* Click the Merge button. Accept the default commit message and merge strategy (merge commit). Click
Merge . You should see that the feature1 branch is now merged. Click on Commits and verify that the
work of feature 1 is now in your commit graph.
* In Bitbucket, navigate to the PullRequest2Fork repository. Select the Source tab. Because of the merge
commit upstream, this repository is 2 commits behind. Click the Sync button on the right (in
Repository details ). Accept the default commit message and click Sync .
* Because the work of the feature1 branch is merged, you can delete the feature1 branch label in the
forked remote repository. You should find the feature1 branch under Branches > Merged
branches.
* Using the command line, delete the local projectjfork repository/directory and create a new clone of
the same name (you may need to delete the existing local folder first). View the commit graph and verify
that the merge commit from upstream is present. Now all of your repositories should be synchronized.


#### Note

Deleting the local repository and recreating it using clone is a choice. Because we knew that all
of our local work has been pushed to the remote repository, we can delete the local repository and
start over using a clone. We are then assured that the remote and local repositories are synchronized.

#### [Remote Repository URL](https://bitbucket.org/MBadriNarayanan/pullrequest2)

#### [Forked Repository URL](https://bitbucket.org/MBadriNarayanan/pullrequest2fork)
