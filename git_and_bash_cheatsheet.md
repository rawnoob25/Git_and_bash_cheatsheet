## Some useful bash and git commands for future reference 

* To list all files tracked by git in (current) working directory, run 
	```bash 
	$ git ls-tree --full-tree -r --name-only HEAD
	``` 
* To change commit message of most recent commit in local git repository in (current) working directory, run 
   ```bash 
   $ git commit --amend -m #<your_commit_message> 
   ``` 