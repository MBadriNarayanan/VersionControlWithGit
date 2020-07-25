### Week 1

#### Installation and Checking version

* Install git
* Check version by typing the command : git --version
* To view current setting for the user name use :  git config user.name
* To change user name, use : git config --global user.name "Your Name"
* To view current setting for the email use :  git config user.email
* To change user email, use : git config --global user.email "Your Email Address"
* To view current setting for the editor :  git config core.editor
* To change editor, use : git config --global core.editor your_preferred_editor

#### Creating Local Repository

* Create a directory : repos
* Navigate to repos and create a directory for the local repository. Let it be "Demo".
* Naviagte to Demo and execute the command : git init
* O/P : Initialized empty Git repository in Demo/.git/
* Check if Demo has a .git directory

#### Commit to Local Repository

* Navigate to Demo directory and execute : git status
* O/P : "Nothing to commit"
* Create an empty file : FileA.txt 
* Execute : git status
* To add FileA.txt to working tree, execute the command : git add FileA.txt
* Execute : git status
* Git adds fileA.txt under "Changes to be committed"
* Commit using: git commit -m "add fileA.txt"
* Check log using : git log (or) git log --oneline for short log

#### Creating a remote repository using bitbucket

##### [Remote Repository URL](https://bitbucket.org/MBadriNarayanan/demorepo)

#### Pushing to remote repository

* Create a remote repository using bitbucket with the name "demorepo" without a README file
* Change the directory to the location of the remote repository and type the command : git remote -v
* Create a README file for the demorepo Repository using echo
* Execute : git add README.md
* Commit using : git commit -m "Your message"
* Push to remote repository using :  git push -u origin master
* Check status using : git status

