# Some useful bash and git commands for future reference 

### Bash 

* To create a hard link (called hard-link) to a file (say f.txt) in working directory, run 
	```bash
	$ ln f.txt hard-link 
	``` 
* To create a soft link (called soft-link) to a file (say f.txt) in working directory, run 
	```bash 
	$ ln -s f.txt soft-link
	``` 

* To print lines 10-15 of file (say f1.R) to terminal, run
   	```bash
   	$ sed -n 10,15p f1.R
   	``` 
* To list only directories within the present working directory, run
	```bash
	$ ls -d */
	``` 

* To prepend to file (say text.txt), run following sequence (copied from https://stackoverflow.com/questions/10587615/unix-command-to-prepend-text-to-a-file):
	```bash
	$ echo "to be prepended" | cat - text.txt > text.txt.tmp
	$ mv text.txt.tmp text.txt
	``` 

* Assuming, extglob is installed, to remove all (including all directories) but a 
  particular file (say, file.txt) from working directory, run 
	```bash
	$ rm -r -- !(file.txt)
	``` 

* To find all .txt files residing inside working directory, run: 
	```bash
	$ find . -name *.txt
	```
See this link for uses of the find program: https://linode.com/docs/tools-reference/tools/find-files-in-linux-using-the-command-line/


### Git

* To list all branches (including remotes), run
	```bash 
	$ git branch -a
	``` 
* To reset the head of a branch (say master) of a remote (say origin) to the parent
(predecessor commit) of a local commit (say 2abc), run:
	```bash
	$ git push origin +2abc^:master
	``` 
In other words, the parent of local commit 2abc has been pushed to the head of 
the remote branch origin/master. The caret ("^")
indicates that we're resetting to the parent of local commit 2abc, the "+" indicates
that we're doing a non-fastforward push (see this link for more info: http://christoph.ruegg.name/blog/git-howto-revert-a-commit-already-pushed-to-a-remote-reposit.html);
the token after push ("origin" in this case) indicates the remote to which we're 
pushing and the token after the colon ("master" in this case) indicates
the branch on the remote to which we're pushing.

* To remove the most recent commit from the currently checked out branch, run:
	```bash 
	$ git reset --hard HEAD^
	``` 
What we're doing is making the head its parent.

* To remove the last 2 commits (that is, the 2 most recent commits) from the
currently checked out branch, run:
	```bash 
	$ git reset --hard HEAD~2
	``` 

* To show diff between a commit (say 2abc) and its parent, run:
	```bash
	$ git diff 2abc^ 
	``` 

* To save commit msg (and subsequently exit commit msg screen)
in built-in Git Bash commit msg editor, type following at editor prompt:
<kbd>ESC</kbd>,<kbd>:x!</kbd>
If you want to exit the commit msg screen without saving the commit (i.e.
you'll be aborting the would-be commit), type following a editor prompt: 
<kbd>ESC</kbd>,<kbd>:q!</kbd> 

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

* To discard all unstaged changes to a specific file (say, t1.txt), run: 
	```bash
	$ git reset HEAD t1.txt
	``` 
* To delete a local branch (say, br_to_del), you must not have it checked out. Check
out another branch and then run:
	```bash 
	$ git branch -d br_to_del 
	``` 
 