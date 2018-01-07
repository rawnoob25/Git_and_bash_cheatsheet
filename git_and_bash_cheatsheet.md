# Some useful bash and git commands for future reference 

### Bash 

* To print lines 10-15 of file (say f1.R) to terminal, run
   	```bash
   	$ sed -n 10,15p f1.R
   	``` 

### Git

* To list all files tracked by git in (current) working directory, run 
	```bash 
	$ git ls-tree --full-tree -r --name-only HEAD
	``` 
* To change commit message of most recent commit in local git repository in (current) working directory, run 
   	```bash 
   	$ git commit --amend -m #<your_commit_message> 
   	``` 
* Suppose you have a remote repository (say on Github) called origin that's ahead of the local branch you're on (say it's the master branch) by some number of commits; assume that all commits in the local branch are also present in the github repository. To update the state of the local repo to match that on github, run 
   	```bash 
   	$ git pull origin master
   	``` 
* To discard all unstaged changes (changes have been made to wdir, but haven't 
yet been adding to staging area), run: 
	```bash 
	$ git checkout -- .
	``` 
	