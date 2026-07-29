---
title: "Git Basics: A Practical Guide to Version Control"
date: 2026-07-29T12:51:28+05:30
draft: false
description: "A foundational guide to mastering Git workflows, branching, and safely navigating commits without losing your repository data, based on the boot.dev curriculum."
tags: 
  - Git
  - Version Control
  - boot.dev
  - Tutorial
categories: 
  - Development
  - Basics
author: "0x-s0M3n4th"
---

> [!Disclaimer]
> This a short version inspired from the course offered by `Boot.dev`. If you want a more interactive , hand holding pathway towards git i would 100% recommend their coursework named as `Learn Git`. Do check that our if you have never heard about them, they really good. I can tell because i have tried their many courses personally. Not a paid promotion btw.

# Basics:
_We will be covering some basic things about git first then deep dive into git internals(Internals part is not covered in boot.dev’s curriculum in a depply manner)._ That i will share separately as a single blog in my website. Now we will only learn the basics here.
## Porcelain and plumbing:
- In git, commands are divided into high level commands → aka **porcleain**, and low level commands → aka **plumbing**.
- We will mostly use **porcleain** commands to interact with either any of our codebases.
- Some of the **porcleain** commands are:
	- `git status`
	- `git add`
	- `git init`
	- `git commit`
	- `git push`
	- `git pull`
	- `git log`
- Some of the **plumbing** commands are:
	- `git apply`
	- `git commit-tree`
	- `git hash-object`
## Git config:

> [!Important]
> Make sure you have `git` installed, there are numerous tutorials available plus you can simply refer to the official docs for the installation part as per your OS. Then open terminal and run `git version` , you should have a version that is `>2.46.0` , if not please upgrade before proceeding.

**What’s the need of configuring git before hand?**
- First of all `git` comes with 3 configuration files → *global*, *local* , _system_. Now they both contain certain information about our ownselves that who we are. Whenver code changes, git can track who made the changes using that configuration file.
- Also to ensure that we get proper credit for our own written code(**Blame** in git’s words), we need to set our `name` and `email` into the config files. 

> [!Note]
> Most of the times we will be using `global` config. The difference between these files is that as the name says `local` config is the configurations for project level changes, it is stored inside individual projects(Having the top most priority → overrides every other configs). `Global` config is used only if something is missing inside `local` config. The `system` config is a machine wide fallback, we can ignore this for now. we will be seeing mostly the `global` config next.

- Let’s start with our configuration of setting up our identity inside git:
	- Open terminal , then check if `user.name` and `user.email` are already set using the following command:
	  ```bash
	  git --no-pager config get user.name # For username
	  git --no-pager config get user.email # For email
	  ```
	  - If not set use the following commands to set them up:
	    ```bash
	git config set --global user.name "github_username_here"
	git config set --global user.email "email@example.com"
	# we can change the config using the same commands with updated details.
	    ```
	    - Instead of `github` username you can use your own name too, whatever you prefer.
	- Setting our default branch to work on → we will set `main` as our default branch, but you can initially set it up as `master`. For context: `git` uses `master` by default but `github` uses `main` by default.
	  ```bash
	  git config set --global init.defaultbranch main # for main
	  git config set --global init.defaultbranch master # for master
	  ```
	- Verify the setup:
	  ```bash
	  cat ~/.gitconfig
	  # or use this
	  git config list --local # for local config
	  git config list --global # for global config
	  ```
	  ![git_1](/images/Git_basics/git_1.png)
	- If you don’t want to see all the values, we can filter that using the `get` command:
	  ```bash
	  git config get <KEY>
	  git config get user.name
	  ```
	- If we need to unset any configuration value, we can use the `unset` command:
	  ```bash
	  git config unser <KEY>
	  ```
	- If there are multiple values of a single key like for `user.name` you have set 3 different values, then we can purge all of them in one go:
	  ```bash
	  git config unset --all <KEY>
	  ```
	- If you want to remove an entire section from your configuration:
	  ```bash
	  git config remove-section <SECTION>
	  ```
### Git configuration locations:
- **System**: `/etc/gitconfig` →  a file that configures Git for all users on the system.
- **Global**: `~/.gitconfig`, a file that configures Git for all projects of a user.
- **Local**: `.git/config`, a file that configures Git for a specific project.
- **worktree**: `.git/config.worktree`, a file that configures Git for part of a project.
### Git configuration overriding:
- If you set a configuration in a more specific location, it will override the same configuration in a more general location. For example, if you set `user.name` in the local configuration, it will override the `user.name` set in the global configuration.
  ![git_2](/images/Git_basics/git_2.png)
<center>CREDIT: Boot.dev</center>
## Setting up repo:
- The very first step of any project is to create a repository. A Git "repository" (or "repo") represents a single project.
- A repo is just a directory that holds all of the files and folders of our project. It contains a hidden `.git` directory which holds internal tracking and versioning information of our project.
- So to setup the repo , first create a directory/folder in your favourable location:
  ```bash
  mkdir first-repo
  cd first-repo
  ```
- Now after moving into the directory, initialise `git`:
  ```bash
  git init
  ```
- After the initialization, you will have a hidden `.git` directory. That you can check using the following command:
  ```bash
  ls -a # <-a> flag shows all the hidden files on our current directory
  ```
  ![git_3](/images/Git_basics/git_3.png)
## Status:
- A file can be in many different states inside a git repository. The most important states are:
	- `Untracked`: Not being tracked by git.
	- `staged`: Marked for inclusion in the next commit.
	- `committed`: Saved to the repository's history.
- Now how we will see the state of our repo? To see that we can use the following command:
  ```bash
  git status
  ```
  ![git_4](/images/Git_basics/git_4.png)
> [!Disclaimer]
> In your case, the results may differ because you are starting with a new repo. Ignore the results , don’t let those intimidate you. Yours repo should show nothing for now.
- To see changes, create a dummy file and name it let’s say `README.md`:
  ```bash
  touch README.md
  # Then again check the status
  git status
  ```
  - This time it should show an untracked file named as `README.md` inside the state of your git repo.
### Staging:
- To add the `untracked` file into our repo `index` , we can use the following command:
  ```bash
  git add README.md
  # we can provide a relative path of a file too, rather than a file name
  git add git-test/i-use-arch-btw/README.md
  ```
  - Without staging, no files are included in the commit – only the files you explicitly git add will be committed.
### Commit:
- A `commit` is a snapshot of the repository at a given point in time. It's a way to save the state of the repository, and it's how Git keeps track of changes to the project. A commit comes with a message that describes the changes made in the commit.
- Here’s how we can made a `commit`:
  ```bash
  git commit -m "YOUR_MESSAGE_ABOUT_THE_CHANGES_YOU_ARE_COMMITING"
  ```

> [!Info]
> We can change our last commit(if we screwed up of course) using the following command : `git commit --amend -m "YOUR_NEW_UNSCREWED_MESSAGE"` 
### Git log:
- A Git repo is a (potentially very long) list of commits, where each commit represents the _full state of the repository_ at a given point in time.
- The `git log` command shows the history of the commits done by you in a repo. Via the logs we can see that → who made the commit, when the commit was made, what was changed.
- Each commit has a unique identifier called a "commit hash" like this `343cdc6121cc032a31004e61f745307b7acbad26`. For convenience, you can refer to any commit or change within Git by using the first `7`characters of its hash. For mine, that's `343cdc6`. 
- To check the logs you can use the following command:
  ```bash
  git --no-pager log -n 10
  ```
  - `--no-pager` : This will paste the logs onto your current static terminal window only, rather than opening something interactive window like `less/more` 
  - `-n` : This will limit the number of lines from your logs output, in this case we are only fetching the first `10` lines from our logs.
- Other useful flags:
  ```bash
 git log --decorate=full # by default
 git log --decorate=short
 git log --decorate=no
 git log --oneline # more compact view of the output  
 git log --oneline --graph --all # shows a nice ASCII art with parent hashes of commit hashes
  ```
- Also `git` stores all of your commits locally as objects inside `.git/objects` .  A commit is just an object. Which we can see using the following command:
  ```bash
  find .git/objects -type f
  ```
 ![git_5](/images/Git_basics/git_5.png) 
- If you want to see the contents of a particular commit you can see that using this command:
  ```bash
  ls -al .git/objects/<COMMIT-INITIAL>/<COMMIT-HASH>
  ls -al .git/objects/a8/7a5e851ac246528fa29156528afa4838e7bcec
  ```
- You should see Compressed RAW bytes. We can convert it into a hexdump so that, atleast we can understand the some headers stuff(LARPING):
  ```bash
  xxd .git/objects/a8/7a5e851ac246528fa29156528afa4838e7bcec
  ```
  ![git_6](/images/Git_basics/git_6.png)
# Git internals(It won’t be that deep):
## Commit-hash:
- My latest commit hash is this `a87a5e851ac246528fa29156528afa4838e7bcec`. You may notice even though we put same content inside the same named file, the commit hash will be different for both of us. The reason behind this is that even though the `commit hashes` are being derived from the content changes of the file , there’s some additional stuff that affects the end hash like:
	-  The commit message
	- The author’s name and email
	- The date and time
	- Parent(previous) commit hashes
- Git uses a cryptographic hash function called `SHA-1` to generate the commit hashes.
## cat-file:
- Git has a buil-in `plumbing` command called as `cat-file` , that allows us to see the contents of a commit hash without needing to LARP around with the object files directly:
  ```bash
  git cat-file -p <COMMIT-HASH>
  git cat-file -p a87a5e851ac246528fa29156528afa4838e7bcec
  ```
  ![git_7](/images/Git_basics/git_7.png)
  - `-p` : It pretty prints the output.
## Trees and Blobs:
`Tree`: The way git uses to store directory.
`Blobs`: The way git uses to store files.
- If we see our `git cat-file` output on the previous section:
  ![git_8](/images/Git_basics/git_8.png)
  - We can see certain details like:
	  - `tree` object along with it’s hash.
	  - The `author`
	  - The `committer`
	  - The commit message.
- Still we can’t see the contents of our file which we commited. Because it’s stored inside a `blob` and the blob is stored inside the `tree`.
- To see the contents follow the steps:
	- Copy the `tree` object’s hash and use it with `git cat-file`:
	  ```bash
	  git cat-file -p <TREE-HASH>
	  ```
	  ![git_9](/images/Git_basics/git_9.png)
	- Now don’t get overwhelmed if you don’t have a lot of blobs, you may have one or more than mine. Choose the hash of the `blob` you want to see the content of and use it again with `git cat-file`:
	  ```bash
	  git cat-file <BLOB-HASH>
	  ```
	  ![git_10](/images/Git_basics/git_10.png)
## Data storage:
- Git stores an entire _snapshot_ of files on a _per-commit_ level.
- **OPTIMIZATION**:
	- To optimize the storing of data , git compresses and packs files.
	- Git deduplicates files that are the same across different commits. If a file doesn't change between commits, Git will only store it once.
# Git branching:
- `Git branch` allows us to keep track of different changes separately.
- Let’s say we have a big project where we are making a game and we need to add a new feature like `shooting the enemy`. So instead of changing the whole project entirely, we can create a new branch out of the `main` branch/ `master` branch called as `shooting_mechanism` . Then when we are done making the feature we can simply merge that branch into the `main` branch to keep the changes. In case if you don’t like the changes , you can simply remove the `shooting_mechanism` branch and go back to the `main` branch.
- **BRANCH UNDER THE HOOD:**
	- A branch is just a named pointer to a specific commit.
	- When you create a branch, you are creating a new pointer to a specific commit. The commit that the branch points to is called the tip of the branch.
	  ![git_11](/images/Git_basics/git_11.png)
	  <center>CREDIT: Boot.dev</center>
	- Because a branch is nothing but a pointer to a commit, they are extremely lightweight and cheap resource-wise to create.
- To check your `branch` use the following command:
  ```bash
  git branch
  ```
  ![git_12](/images/Git_basics/git_12.png)
## Renaming a branch:
```bash
git branch -m <old-name> <new-name>
git branch -m master main
```

## Creating a branch:
- There are 2 ways to create a branch:
	- First:
	  ```bash
	  git branch <NEW_BRANCH_NAME>
	  ```
	- Second:
	  ```bash
	  git switch -c <NEW-BRANCH-NAME>
	  ```
	  - The `switch` command allows us to switch branches. Including the `-c` flag tells Git to create a new branch and switch to it.
- If we want to create a branch off of some other commit, other than the latest one, say for example there are 3 commits in `main` branch → `A, B, C`, i want to create a branch from `B`  we can use the following command:
  ```bash
  git -c switch <new_branch_name> <COMMIT_HASH_OF_B_COMMIT>
  ```
  - You can get the `COMMIT_HASH` of any commit using the `git log --oneline` command. Check from where you want to create a branch accordingly.
- When you create a new branch, it uses the _current commit_ you are on as the branch base.
- Let’s say we are having a main branch of 3 commits → Commit `A, B, C`. Then we are creating a new branch named as `new_branch`.  As `C` is the last commit of `main branch` , the `new_branch` will be a pointer to that `C` commit, when we will run `git switch -c new_branch` .The visualization will look like this:
  ![git_13](/images/Git_basics/git_13.png)
> [!Note]
> We can switch to an another branch using `git switch` and there’s another old command which is being used by many devs that is `git checkout`. Syntax of the command is `git checkout <new-branch-name>`. It is advised to use `git switch` because why not it’s kind of better and having a well put name for switching branches.

- When we will make a commits over to our `new_branch`, let’s say we did one commit `D` . Then the branch will look something like this:
  ![git_14](/images/Git_basics/git_14.png)
# Git files:
- As we know git stores all of the information in files inside `.git` subdirectory at the root of our project, even information about branches.
- The "heads" (or "tips") of branches are stored in the `.git/refs/heads` directory. It contains one file for each branch and the branch files are containing their respective `commit hash` that the branch points to.  
- Seeing the `commit hash` of the branch tips, let’ see our `main` branch:
  ```bash
  cat .git/refs/head/main
  # if you have branches you can see those hashes too.
  ```
  ![git_15](/images/Git_basics/git_15.png)
- After getting the commit hash we can see the properties of that hash using `git cat-file` as well as we can find it’s object location inside `.git` directory:
  ```bash
  find .git -name "a8"
  git cat-file -p <HASH_VALUE>
  ```
  ![git_16](/images/Git_basics/git_16.png)
  ![git_17](/images/Git_basics/git_17.png)
# Git merge:
- Let’s say we are in this stage where we are having 2 branches → `main` with 3 commits and `new_branch` with 2 commits:
  ![git_18](/images/Git_basics/git_18.png)
- Now if i merge `new_branch` into `main` git combines both the branches by creating a new commit that has both histories as parents:
  ![git_19](/images/Git_basics/git_19.png)
<center>Merging to main  </center>
- Here `F` is a merge commit that has both `C` and `E` as parents. `F` brings all the changes from `D` and `E` back into the `main` branch. Command used to merge onto main:
  ```bash
  git switch main # switching to main
  git merge new_branch
  ```
- When we run this command these are the following things that happen under the hood:
    1. Find the "merge base" commit, or "best common ancestor" of the two branches. In this case, `B`.
	2. Replay the changes from `main`, starting from the best common ancestor, into a new commit.
	3. Replay the changes from `new_branch` onto `main`, starting from the best common ancestor.
	4. Records the result as a new commit, in our case, `F`.
	5. `F` is special because it has _two parents_, `C` and `E`. Means it points towards both of those commits.
![git_20](/images/Git_basics/git_20.png)
<center>Merging to new_branch</center>
- When we will be merging the branch we can merge from the `main`  or vise-versa using the following command:
  ```bash
  git switch main
  git merge new_branch # merging new_branch from main branch
  ```
- Let’s see a bit complex setup:
![git_21](/images/Git_basics/git_21.png)
<center>Multiple merges</center>
- In the above diagram we can see we have already merged once from `new_branch` , after that `main` branch created 2 more new commits. Then i decided that i want to merge my `new_branch` onto the `main` branch. It resulted 2 new commit objects with their respective `COMMIT_MSG` . We merged using the following command from main:
  ```bash
  # previously we were on new_branch
  git switch main
  # made 2 new commits
  git merge new_branch # merged new_branch from main
  ```
## Tips: if you mess up the commit message and want to change it:
- We can change the `commit message` if we have messed it up using the `--amend` option:
  ```bash
  git commit --amend -m "F: Merge branch 'new_branch'"
  ```

> [!Info]
> If you don’t prefer vim as your default editor for writing messages, you can do that using the following commands:
> **If you want to set VS code as the default editor:** `git config --global core.editor "code --wait`
> **If you want to set zed as your default editor:** `git config --global core.editor "zed --wait"`
## Fast-forward merge:
- This is the simplest type of merge.
- Let’ say we are having this:
  ![git_22](/images/Git_basics/git_22.png)
  - Now if we merge from `main` using the command:
    ```bash
    git merge branch_1
    ```
    - Just because `branch_1` is containing all the commits that `main` branch has, git automatically does a fast-forward merge. It just moves the pointer of the "base" branch to the tip of the "branch_1" branch like this:
      ![git_23](/images/Git_basics/git_23.png)
    - In `fast forward merge` , no merge commit is created. On the above scenario the `head` pointer is pointing to `main` after merging. 
    
>[!Important]
>From which branch i will be merging the head will point to that branch only.

  - Another common point of confusion is that let’s say what will happen if the branch we are working on is having multiple commits and what will happen if `main` branch moves forward with multiple commits, let’s see both the scenarios:
    - **When branch_1 will have multiple commits, and main branch is behind with not further commits**:
      ![git_24](/images/Git_basics/git_24.png)
	    - Now if i merge the `branch_1` from `main` , it will perform a fast forward merge still. Reason being in the perspective of `main` the `branch_1` is already having the commits that `main` branch has.  Here also git will move the pointer of the base branch which is `main` to the tip of `branch_1` :
	      ![git_25](/images/Git_basics/git_25.png)
	- **When main branch will have commits along with the branch_1**:
		![git_26](/images/Git_basics/git_26.png)
		- It won’t be a fast forward merge, because now our `branch_1` doesn’t know about the commit `F, G, H`, means it doesn’t have all the `main` branch’s commits.

> [!info] 
> Always keep your `main` branch behind of your other branches if you want to do a fast forward merge.

## Common developer workflow for merging:
1. Create a branch for a new change
2. Make the change
3. Merge the branch back into `main` (or whatever branch your team dubs the "default" branch)
4. Remove the branch
5. Repeat
# Git rebase:
- When we rebase it doesn’t create any merge commits. It simply replays the commits from another branch on top of main. Let’s take a scenario:
	- Let’s say we are having 4 commits in our `main` branch, and we have created a branch off of the 2nd commit from `main` branch. That branch is also having 2 commits like this:
	  ![git_27](/images/Git_basics/git_27.png)
	- We are on the `feature_1` branch. To bring changes from `main` onto the current branch `feature_1`, we will use this command:
	  ```bash
	  git rebase main
	  ```
	  This will do the following:
		1. Identify the latest commit from `main` and use it as the temporary new base for the rebase process
		2. Replay each commit from `feature_1` one at a time onto this temporary location
		3. Update the `feature_1` branch to point to the last replayed commit in the temporary location, making this the new permanent `feature_1`
		4. The rebase does _not_ affect the `main` branch; `feature-1` now includes all changes from `main`.
	- The current branch will look like this after rebase:
	  ![git_28](/images/Git_basics/git_28.png)
	- We can see there’s no additional `commit` is being made during rebase. Also we will be having a linear history if we do a `git log --oneline` to check.

> [!Important]
> **When to use Merge and when to use rebase?**
> An advantage of merge is that it preserves the true history of the project. It shows when branches were merged and where. One disadvantage is that it can create a lot of merge commits, which can make the history harder to read and understand.
> A linear history is generally easier to read, understand, and work with. Some teams enforce the usage of one or the other on their `main` branch, but generally speaking, you'll be able to do whatever you want with your own branches.

> [!Warning]
> You should _never_ rebase a public branch (like `main`) onto anything else. Other developers have it checked out, and if you change its history, you'll cause a lot of problems for them.
> However, with your own branch, you can rebase onto other branches (including a public branch like `main`) as much as you want.
# Resetting changes:
## Soft reset:
- We can use the command `git reset` to undo the last commit(s) or any changes in the index (staged but not committed changes) and the worktree (unstaged and not committed changes):
  ```bash
  git reset --soft COMMIT_HASH
  ```
  - The `--soft` option is useful if you just want to go back to a previous commit, but keep all of your changes.
  - Committed changes will be uncommitted and staged, while uncommitted changes will remain staged or unstaged as before.
## Hard reset:
- In the case of `soft commit` we kinda time traveled to the previous commit by preserving our current commits. But in the case of `hard commit` it’s not going to keep the changes:
  ```bash
  git reset --hard COMMIT_HASH
  ```
  - The `--hard` flag makes your working directory and staging area match the specified commit exactly, discarding any local changes.
  - This is useful if you just want to go back to a previous commit and discard all the changes.
> [!Warning]
> Always be careful when you are using `--hard` reset.  If you were to simply delete a _committed_ file, it would be trivially easy to recover because it is tracked in Git. However, if you used `git reset --hard` to undo committing that file, it would be deleted for good.
# Git remote:
- We can have "remotes," which are just external repos with _mostly_ the same Git history as our local repo.
- `Git` is just the CLI tool, there’s isn’t any central repo . Github is just someone else’s repo.
- In git, another repo is called a "remote." The standard convention is that when you're treating the remote as the "authoritative source of truth" (such as GitHub) you would name it the "origin".
- Syntax:
  ```bash
  git remote add <name> <uri>
  ```

> [!Info]
> We can refer a local different repo as remote as well. Git will treat other git repos as remote .

## Git fetch - for local repos:
- Adding a remote to our Git repo does _not_ mean that we automagically have all the contents of the remote. First, we need to fetch the contents:
  ```bash
  # Run this from the new repo you created, where you want to fetch other repo's contents
  git fetch origin
  ```
- Just because we fetched all of the metadata from the remote `webflyx` repo doesn't mean we have all of the files. We can confirm this via running `git log` , we will get to see that there’s no commits in the logs.

> [!Info]
> We can log the commits of a remote repo as well using `git log <remote>/<branch>` → `git log origin/main`
## Merging branches between local and remote repo:
- For example: if i want to merge the `feature_1` branch of the remote `origin` into our local `main` branch, i would run this inside the local repo:
  ```bash
  git merge origin/feature_1
  ```
- Because the local repo is currently empty and branch is also empty → means we are behind the remote branch. We will get to see a `fast forward` merge instead of a `commit merge`.
# .gitignore:
- Sometimes w don’t want to track some crucial files under `git` , because we may put those on the internet unknowingly. To prevent that mistake, we can utilize the file `git` offers which is `.gitignore`.
- For example, if you work with Python, you probably want to ignore automatically generated files like `.pyc` and `__pycache__`. If you are building a server, you probably want to ignore `.env` files that might hold private keys. If you (I'm sorry) work with JavaScript, you might want to ignore the `node_modules` directory.
- Inside the `.gitignore` file we can add files like this to ignore them:
  ```text
  node_modules
  .env
  ```

> [!Note]
> You can use regex patterns to match multiple files all at once . Be careful with them if you don’t know how to use regex, specify the specific file paths. But when you will be working with a lot of files and folders, learning a bit of regex doesn’t hurt.
## What to ignore?
1. Ignore things that can be _generated_ (e.g. compiled code, minified files, etc.)
2. Ignore dependencies (e.g. `node_modules`, `venv`, `packages`, etc.)
3. Ignore things that are personal or specific to how you like to work (e.g. editor settings)
4. Ignore things that are sensitive or dangerous (e.g. `.env` files, passwords, API keys, etc.)

<center>THIS IS THE END OF THIS TUTORIAL</center>
> [!Note]
> If you want a gamified learning of git or any backend related stuff, i would 100% recommend to check out the Boot.dev’s backend curriculum. Here’s the link ![Boot.dev](https://www.boot.dev/paths/backend?tech=python-golang) 
