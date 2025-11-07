# Git 

	### Config

	
```bash
	git config user.name <username>
	git config user.email <email>
git init
```

	### Status

	`git status`

	![Pasted_image_20230530152714.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b5a29e4-b818-4730-8ee4-77eca8830c79/8cd5e48f-eea8-48aa-9b9f-82b5b8f37c80/Pasted_image_20230530152714.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466SFA5MGXH%2F20251105%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20251105T172517Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMb%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJIMEYCIQDkEZiEpPyvjBs7dDUUNsJUwfqfxJF7HfMr6hmg4c%2FDRQIhAJTPEwmikdwY3winz0VkT6eM80MSoQ0Sq0K6Y3MIp%2BC6KogECI%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQABoMNjM3NDIzMTgzODA1IgyoQrKXnxUaEqdxUEAq3AOa7p%2FY79%2FtWAulqwX4q4YG2mHx%2B74W%2BVMBysnSAWgD6Pd9MXtZK6Rsc1HwkKjyzIQknZG540MkZ4dyvNzoNatxQDGqAH72%2FcfHA6h7PotEf69BBTVcc16PWutnk3DbT2e9zsnl1kykChjhnNwJDL2T28fgnBAT6J5kz1UE9InEBgb9akuq6%2FBnA8gT5NTm3oEg%2BTPi5FgDmFQl7unACyOpB4FEvGXi19LZHkNV6TuUMSn4XNvWyL5e12rPSB5YEOOXqglPTBFwXBWQaoongZMHD9ZmxjcuJT5rVygoz53MzXxbIMLjH2QCGDnQukmJGPDF%2FGZFvJ7AvUzhBebg68Ye%2FU87F9nLX%2BCgT0QhgmT%2BPlxCHwbuooSbCMOxlDXbnFpnJmEEgYC0OAcOt6%2F8Ib0gnBkuwsPOuZygt7QhTRpi9SJd08SvUNLvjQdO03fi7vYksTKRKJstgmQs4%2Baa1COuW1Y%2BdKAAvoPNaj%2ByfDHlcXVSL%2B%2FtfQcCZq%2FXW7jExBEztRDDdcxukuVB%2Fm3ctlS%2FT0P3sSg2nPq0DAUwDBaKo1lxfPs4lQUay52Jrr2%2FiuhNfJNhv8XcW3Pyc8tut%2F8eNQ%2B%2F%2BZP8LX3ID5GrlH1JQBE0IsSk65M0MIpd2jDbrK3IBjqkAempI0JTHgeKRPQ0I%2BQQKjnJjnHy8xInd7skU46P7agu1mcyJyaTk81qMYSNZLnht5SUaQoTVYYFdPcA42vaImGO8X01M0%2BKlmyQa6aMqsRWy%2Fj8m%2FHZNSfWxoyy0QWCvS49lge%2F%2B%2FGmrq5NoK7nXRVHGrQ%2FfV45yiugQlr5rpx4vePKzlMmWD43xtFeqDI%2BRSUVHFER5URg2QCGFjfGNnUan1Tu&X-Amz-Signature=a62a1f993e23cc2fafaf55d371ab4860eee0175778ba67cea51fbc74d52b4ec9&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

	### Shorthand Status

	`git status -s`

	![Pasted_image_20230530155456.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b5a29e4-b818-4730-8ee4-77eca8830c79/c6b79f54-45b7-44b9-bc0e-e86af70ecdad/Pasted_image_20230530155456.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466SFA5MGXH%2F20251105%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20251105T172517Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMb%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJIMEYCIQDkEZiEpPyvjBs7dDUUNsJUwfqfxJF7HfMr6hmg4c%2FDRQIhAJTPEwmikdwY3winz0VkT6eM80MSoQ0Sq0K6Y3MIp%2BC6KogECI%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQABoMNjM3NDIzMTgzODA1IgyoQrKXnxUaEqdxUEAq3AOa7p%2FY79%2FtWAulqwX4q4YG2mHx%2B74W%2BVMBysnSAWgD6Pd9MXtZK6Rsc1HwkKjyzIQknZG540MkZ4dyvNzoNatxQDGqAH72%2FcfHA6h7PotEf69BBTVcc16PWutnk3DbT2e9zsnl1kykChjhnNwJDL2T28fgnBAT6J5kz1UE9InEBgb9akuq6%2FBnA8gT5NTm3oEg%2BTPi5FgDmFQl7unACyOpB4FEvGXi19LZHkNV6TuUMSn4XNvWyL5e12rPSB5YEOOXqglPTBFwXBWQaoongZMHD9ZmxjcuJT5rVygoz53MzXxbIMLjH2QCGDnQukmJGPDF%2FGZFvJ7AvUzhBebg68Ye%2FU87F9nLX%2BCgT0QhgmT%2BPlxCHwbuooSbCMOxlDXbnFpnJmEEgYC0OAcOt6%2F8Ib0gnBkuwsPOuZygt7QhTRpi9SJd08SvUNLvjQdO03fi7vYksTKRKJstgmQs4%2Baa1COuW1Y%2BdKAAvoPNaj%2ByfDHlcXVSL%2B%2FtfQcCZq%2FXW7jExBEztRDDdcxukuVB%2Fm3ctlS%2FT0P3sSg2nPq0DAUwDBaKo1lxfPs4lQUay52Jrr2%2FiuhNfJNhv8XcW3Pyc8tut%2F8eNQ%2B%2F%2BZP8LX3ID5GrlH1JQBE0IsSk65M0MIpd2jDbrK3IBjqkAempI0JTHgeKRPQ0I%2BQQKjnJjnHy8xInd7skU46P7agu1mcyJyaTk81qMYSNZLnht5SUaQoTVYYFdPcA42vaImGO8X01M0%2BKlmyQa6aMqsRWy%2Fj8m%2FHZNSfWxoyy0QWCvS49lge%2F%2B%2FGmrq5NoK7nXRVHGrQ%2FfV45yiugQlr5rpx4vePKzlMmWD43xtFeqDI%2BRSUVHFER5URg2QCGFjfGNnUan1Tu&X-Amz-Signature=e88208816430d62dd78661539e1acecbbd280ba39a5ce7eca09e1bd54862a8cc&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

	### Create

	To Create an empty file - `touch <file>.extn`  like .html or .py or .cpp

	### Staging

	`git add <FILE> `or` ``**git add -A**`

	### Commit

	- `git commit <FILE> `

	- `git commit -a -m "<SKIP STAGING AREA>"`      (***Not recommended***)

	- `git commit -m "MESSAGE"`

	### gitignore

	- `touch .gitignore*.log`      (*Ignores all the files with this ext.*)

		- `log/`     ('/'* this tells git that it's a directory, & to ignore it)*

	### git diff

	- Shows difference between working directory and stage - `git diff`

	- To see diff between stage and the last commit - `git diff --staged`

	### Restoring

	- `git restore <FILE> `

	- `git restore -f`

	### Logs

	- `git log -p -<no. of last commits to see>`

	### Removing

	- `git restore --staged <FILE>`      (*Remove from Stage, Make it untracked*)

	- `git rm <FILE>`     (*Remove from HDD as well as git*)

	### Branch

	- `git branch <branch name>`     (*creates a branch*)

	- `git checkout <branch name>`     (*switches to the branch)*

	- `git checkout -b <branch name>`     (*creates a new branch and also switches to it)*

	### Merge

	- switch to the branch
`git merge <some other branch>`     (*present branch and selected branch gets merged*)

	<br/>

	### Clone

	- `git clone https://github.com/libgit2/libgit2` this clone in a new directory within called `libgit2`  

	- `git clone ``[https://github.com/libgit2/libgit2](https://github.com/libgit2/libgit2)`` mylibgit`  this clones at location, in a dir named `mylibgit` in arg, and inside a `libgit2` directory

# GitHub

	### Add Repository

	- `git remote add orgin <SSH URL>`     (***origin ****is alias of the repository*)

	- fetch and push URL can be obtained by - `git remote -v`

	### Getting GitHub Repo Setup

	- `ssh-keygen -t rsa -b 4096 -C "kanishk.kumar412@gmail.com"`

	- `eval $(ssh-agent -s)`

	- `ssh-add ~/.ssh/id_rsa`

	- `cat ~/.ssh/id_rsa.pub`     (*prints the key*)

	- create a new SSH key in GitHub, with the above obtained key.

	- Set new SSH URL - `git remote set-url origin <SSH URL>`

	### Push

	- Switch to the branch to push `git push -u <repo name> <branch name>`

	- `git push -u {branch name}`      (this stores the command after -u for quick use by command `git push)`

# Maintaining Multiple Repos on a single machine

	### 1. Copy over the already generated SSH keys ;

	- `id_rsa` = private key

	- `*.pub` = public key (which is added into github or AUR)

	- `kanishk_github` = private key for (KanishkMishra143)

	- `kanishk_github.pub` = public key for (KanishkMishra143)

	### 2. Setting proper permissions

	
```javascript
cd ~/.ssh

# Set folder permissions
chmod 700 ~/.ssh

# Private keys (restrict to user only)
chmod 600 id_rsa
chmod 600 gitlab_key
chmod 600 collab_kanishk
chmod 600 kanishk_github

# Public keys (readable by everyone)
chmod 644 id_rsa.pub
chmod 644 gitlab_key.pub
chmod 644 collab_kanishk.pub
chmod 644 kanishk_github.pub

# Config and known hosts
chmod 644 config
chmod 644 known_hosts
chmod 644 known_hosts.old

# Fix ownership in case it got copied as root or another user
sudo chown -R $USER:$USER ~/.ssh
```

	### 3. Global Config

	- `git init` (If required)

	- `git config —global ``[user.email](http://user.email/)`` <email.@gmail.com>`

	- `git config —global user.username <username>`

	### 4. Local Config (New Local repo)

	- `git init`

	- `git config ``[user.email](http://user.email/)`` <email.@gmail.com>`

	- `git config user.username <username>`

	### 5. New Repository

	- Make a repository on Github without LICENSE or README

	- `git remote add origin <ssh-url> `(first time origin setup to remote repo)

	- `git remote set-url origin <ssh-url>` (for correcting origin url after it is set the first time)

	- `git push -u origin main`  (`-u` saves origin and main, so that `git push` can be used for easy use)

[//]: # (link_to_page is not supported)

<br/>

