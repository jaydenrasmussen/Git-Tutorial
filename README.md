# **git**

> the stupid content tracker

Git was created by Linus Torvalds in 2005 as a way to track the source for the linux kernel.

### The Basics

Git internally works like a big hash map. It creates a hash of the current files, the changes that occured, the time that they occurred at and who made the changes (according to their email/name). Then, it points to a record locally of those changes. Further reading: https://medium.com/@shalithasuranga/how-does-git-work-internally-7c36dcb1f2cf

https://git-school.github.io/visualizing-git/

https://www.atlassian.com/git/tutorials

NOTE: For more detail on any of these verbs you can apply the `--help` flag for the manual page

##### Common Commands

- `add` - adds files to be commited
- `commit` - creates a record of the staged files to the repo (locally)
- `checkout` - gets a specific reference to a file/directory/commit
- `log` - prints out a log of all the commits for that repository (`q` to quit).
- `push` - syncs the commits that were made locally to the remote
- `pull` - syncs the local repository with the changes that exist in the remote
- `reset` - unstages files that were made locally to a commit/hash
- `branch` - creates and lists branches
- `merge` - merges branches or commits together
- `status` - shows the current status of the repo
- `stash` - moves the current changes to a stack to be applied later
- `rm, mv` - remove, move



### Getting More Advanced

- `alias` - Allows you to create shorthand for git commands you use a lot
- `clean` - cleans up your local repository files not tracked by git
  - `git clean -dfx` removes all untracked files in the directory including build products etc. 
    - `-d` directories
    - `-f` force
    - `-x` exclude the gitignore rules
- `rebase` - reapplies commits at the current head (this erases history and is not recommended)
- `revert` - creates a new commit that undoes what a previous commit did
- `bisect` - helps you find bugs at the speed of `O(n log n)`
  - `start` - begins the wizard
  - `good <hash>` -marks the commit as not problematic
  - `bad <hash>` - marks  the commit as bad
  - `reset` - exits the wizard and moves the head back to where it should be

- `cherry-pick` - applies a commit on top of the current head and then moves the head forward to that new commit. Note: this will only apply the changes from that commit
- `tag`  - adds a tag to the current commit. There are two types. lightweight tags (meant for working locally, not pushed by default) and annotated tags, which are pushed out by default and require a message 
- `prune` - removes all unreachable objects from the database
- `show <branch>` - displays the changes from your branch versus another or one commit to another
- `whatchanged` - displays a log of all the files that were touched and the new hashes of those files that were committed
- `blame` - displays who made the commit, at what time that is in the file on a per line basis



### Mastering The Tool

- `patches` 
  - `format-patch` - will output git readable patch information for the changes between one branch and another, or one commit and another
  - `apply` - will add those patches into your branch, this is the manual way to do a merge, but will let you pull out changes that occurred in say, just one commit

- `submodule` - (yo dawg. I heard you like git repos...) This lets you initialize and control repos that exist inside of your repo, but have different urls

- `reflog` - short hand for reference log, which identifies all the internal commands that have been run in the repo

- `remote add -t <branch> -f origin <repourl>` - allows you to clone just a specific branch from a remote, although it does require you to have a blank git repo and a new folder intialized. useful if you want to work on a very small portion of a large project and don't want to take the time to clone all the remote branches

- `rerere` - reuse recorded resolution

- `cherry` - verifies that commits were cherry picked and added to your upstream

- `ls files` - lists all the files tracked by git and their individual hashes

- `credential` - stores your git credentials, the protocol to be used etc.

- `gc` - garbage collection, allow you to remove dangling branches or changes that you backed out of (like a coward).

- `bisect run <script>` - lets you run a script to test whether or not a bug still exists in your codebase during the bisect process. In this way, you can quickly regression test your code base.

  

