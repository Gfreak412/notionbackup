# Git 

	### Config

	
```bash
	git config user.name <username>
	git config user.email <email>
git init
```

	### Status

	`git status`

	![Pasted_image_20230530152714.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b5a29e4-b818-4730-8ee4-77eca8830c79/8cd5e48f-eea8-48aa-9b9f-82b5b8f37c80/Pasted_image_20230530152714.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466WFMRJIEL%2F20251105%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20251105T172247Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMb%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJGMEQCIFnAXzCsrrTVr0DpbfC1p6zhR2rQbnVsP6XVQogPIoMTAiASN56N1DKrM4rCrZSdQ3rd490ybLRI%2FuWPHRgfFfk67yqIBAiP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDYzNzQyMzE4MzgwNSIMzHo7iycOFhEvdTkyKtwDM93YD8GFEenPc5TdMt6M0FRWlmHqQhw3GvXrxaC9voEsIkmksmSF8lNGTXa5bT24H9btr5Bia7Qigb%2FNaaBg0x2TS48QcVab2I5OjjERvpbzriu4h8LjGqf%2FOe%2BaCX0MO06IbrMoxpQK9UzDIYvDCzlX%2FCXn4t3LiuQf2MapAf3qJxPgftXTTfKHSXi54rVTF%2FaDVPrMXuevYu%2BDV0jF1%2FSrc3AenfT5OWdUlbQTqvlQbmN%2FhIJOM52clvrjK0SXNvuEZUfh%2BCcYi70ARxIJid3NUO4cu4mHLp5EBXcOldcIbaNCMy5SyPnBJPgi6G%2FZlPIHQi8Jr3CKTrQifTEsceR2dTiRckb%2FSfZK7nmAL0UIKiDGIhmMarpExjyAi%2BxmeJSjRCXWByLhfFL1ciiIxwvy1BRm0L7xRTmWACkuOrGehVnLsVp0%2FkhaAGxKWr69dB9Cmyrn%2FvMPA3aoj4lUEtMdWdz7Dz3QPO2UDcCjLLdPjWvYkSHV6CAwDBktNu3Y%2FYTJRoDQMvsLyno99eYxJnB2ibLw7qvxWhtYOxEu48ittjRPZR7X4KRwuIV1dB1KiIYllcj1NYCTh7MdSKfdm3nBXYLe6hjOP8ipAmInSOvCk8CIezsi7wcgc5Ew3qytyAY6pgEcJqJP%2Bp9sRAHRSPjDmlZ8fzzCDybqG%2B6ZEGPkqmn1Oa7YlFm27qKUL%2BVdyiDy0L0shKCO218V5%2FmRe1yd6R%2FyonXOfB9jilk%2BRF6uV4yW%2FzrF7GgVIqX%2BVgDYP%2BR%2BlIFGyhp%2BDXVxrxlm2QBa0plelOW5kgVPXZv1qNi11g%2FzloOHK8%2By1yzy6nyPf%2BZYr%2Fpq%2F3%2FBbzpg3JR4DsYD0vFPC2O%2FSdfG&X-Amz-Signature=df7c8f26be248d9062862aaae02a3f40c84a72dda68313372472580a92b37d31&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

	### Shorthand Status

	`git status -s`

	![Pasted_image_20230530155456.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/8b5a29e4-b818-4730-8ee4-77eca8830c79/c6b79f54-45b7-44b9-bc0e-e86af70ecdad/Pasted_image_20230530155456.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=ASIAZI2LB466WFMRJIEL%2F20251105%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20251105T172247Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEMb%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLXdlc3QtMiJGMEQCIFnAXzCsrrTVr0DpbfC1p6zhR2rQbnVsP6XVQogPIoMTAiASN56N1DKrM4rCrZSdQ3rd490ybLRI%2FuWPHRgfFfk67yqIBAiP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAAaDDYzNzQyMzE4MzgwNSIMzHo7iycOFhEvdTkyKtwDM93YD8GFEenPc5TdMt6M0FRWlmHqQhw3GvXrxaC9voEsIkmksmSF8lNGTXa5bT24H9btr5Bia7Qigb%2FNaaBg0x2TS48QcVab2I5OjjERvpbzriu4h8LjGqf%2FOe%2BaCX0MO06IbrMoxpQK9UzDIYvDCzlX%2FCXn4t3LiuQf2MapAf3qJxPgftXTTfKHSXi54rVTF%2FaDVPrMXuevYu%2BDV0jF1%2FSrc3AenfT5OWdUlbQTqvlQbmN%2FhIJOM52clvrjK0SXNvuEZUfh%2BCcYi70ARxIJid3NUO4cu4mHLp5EBXcOldcIbaNCMy5SyPnBJPgi6G%2FZlPIHQi8Jr3CKTrQifTEsceR2dTiRckb%2FSfZK7nmAL0UIKiDGIhmMarpExjyAi%2BxmeJSjRCXWByLhfFL1ciiIxwvy1BRm0L7xRTmWACkuOrGehVnLsVp0%2FkhaAGxKWr69dB9Cmyrn%2FvMPA3aoj4lUEtMdWdz7Dz3QPO2UDcCjLLdPjWvYkSHV6CAwDBktNu3Y%2FYTJRoDQMvsLyno99eYxJnB2ibLw7qvxWhtYOxEu48ittjRPZR7X4KRwuIV1dB1KiIYllcj1NYCTh7MdSKfdm3nBXYLe6hjOP8ipAmInSOvCk8CIezsi7wcgc5Ew3qytyAY6pgEcJqJP%2Bp9sRAHRSPjDmlZ8fzzCDybqG%2B6ZEGPkqmn1Oa7YlFm27qKUL%2BVdyiDy0L0shKCO218V5%2FmRe1yd6R%2FyonXOfB9jilk%2BRF6uV4yW%2FzrF7GgVIqX%2BVgDYP%2BR%2BlIFGyhp%2BDXVxrxlm2QBa0plelOW5kgVPXZv1qNi11g%2FzloOHK8%2By1yzy6nyPf%2BZYr%2Fpq%2F3%2FBbzpg3JR4DsYD0vFPC2O%2FSdfG&X-Amz-Signature=d3fb9bc02bae2aeef1932058e898b626e7c93ce1131d940ad2362679e15980cd&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)

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

