# Alx-pre_course

This is a simple repository where we are introduced to Git, Github, and source code management. I will be using this readme to explain these concepts

### What is source code management?
**Source code management (SCM)** is used to track modifications to a source code repository. SCM tracks a running history of changes to a code base and helps resolve conflicts when merging updates from multiple contributors. SCM is also synonymous with **Version control (VC)**.

VC lets developers safely work through **branching** and **merging**.

With branching, a developer duplicates part of the source code (called the repository). The developer can then safely make changes to that part of the code without affecting the rest of the project.

Then, once the developer gets his or her part of the code working properly, he or she can merge that code back into the main source code to make it official.

All of these changes are then tracked and can be reverted if need be.


### What is Git?
**Git** is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. Unlike most other Version Control Systems (VCSs), git stores each saved version as a ‘snapshot’ instead of a list of changes made to each file. You can reference old snapshots whenever you need to and new snapshots are created when your project is modified.

However, there are a few drawbacks to handling development this way. As local software installed on your individual machine, git cannot read the edits other developers may be making in real-time. This means that if you and a teammate are working on a project simultaneously, you won’t be able to view each other’s work.

### What is GitHub
**GitHub** is a website and cloud-based service that helps developers store and manage their code, as well as track and control changes to their code. It also includes project organization and management features. You can assign tasks to individuals or groups, set permissions, and roles for collaborators, and use comment moderation to keep everyone on task. Github repositories are publicly available, meaning developers from across the globe can interact with and contribute to each other's code in order to modify or improve it, known as **social coding**.

There are three primary actions you can take when it comes to interacting with other developers’ code on GitHub:

- **Fork:** The process of copying another’s code from the repository in order to modify it.
- **Pull:** When you’ve finished making changes to someone else’s code, you can share them with the original owner via a ‘pull request’.
- **Merge:** Owners can add new changes to their projects via a merge, and give credit to the contributors who suggested them.

### What is the difference between Git and GitHub
GitHub makes it easier to collaborate by incorporating git's VC features. It’s a platform that can hold repositories of code in cloud-based storage so that multiple developers can work on a single project and see each others’ edits in real-time. Conversely, git is a local VCS software that enables developers to save snapshots of their projects over time. It’s generally best for individual use.

**Before proceeding, lets define a few terms:**

- **Repository:** The file location where your project is stored.
- **Commit:** The command used to save new changes to your project in the repository.
- **Stage:** Before you can commit changes in Git, you need to stage them – this gives you the chance to prepare your code before formally adding it to your project.
- **Branch:** The part of your project you’re actively developing.
- **README.md:** a markdown document that serves as the introductory guide to your project. It's the first thing people see when they visit your repository on platforms like GitHub. It's a way to communicate with potential users, collaborators, and contributors.

### How to create a repository
Prerequisites is to have Git installed locally on your machine and a created GitHub account. If you want to set up your repository locally, then all you need to do is to initialize the repository as a git repo. You typically obtain a Git repository in one of two ways:
1. You can take a local directory that is currently not under version control, and turn it into a Git repository, or

2. You can clone an existing Git repository from elsewhere.


To do (1), navigate to the directory you want your repository to be in and in the command line type

```
git init
```

which will initialize the parent repository as a git repo and will track all changes.

#### To integrate the repository with Gitub, i.e. (2):

1. First we must create a repository on GitHub. Give it a descriptive name. Follow the instructions on the page. If we wish to make it private, we select that in the options, but mostly we're gonna want to opt for the public repo.
2. We can also add a README.md and .gitignore but I prefer doing that locally so lets keep it unchecked
3. Now we have two choices, either create a new repository on the CLI or push an existing one. Assuming we've used `git init` on a local directory.

#### To create a new repository
```
cd /path/to/your/directory
git init
git config --global user.name <name>
git config --local user.email <email>
echo "# Some text" >> README.md
git add .
git commit -m "some message"
git remote add origin https://github.com/user_name/repo_name.git
git push -u origin master
```


#### To push an existing repository
use the last 2 commands from the previous section, namely:
```
git remote add origin https://github.com/user_name/repo_name.git
git push -u origin master
```
### How to pull updates
If there are any changes in the remote branch that aren't relected in your local repository, you can:
```
git pull origin master
```
### Git branching
Branching means you diverge from the main line of development and continue to do work without messing with that main line. The way Git branches is incredibly lightweight, making branching operations nearly instantaneous, and switching back and forth between branches generally just as fast.

#### How to create a branch
```
git branch branch_name
```
We can switch to the branch using 
```
git checkout branch_name
```
a way to do both in one go is
```
git checkout -n branch_name
```
to view the branches 
```
git branch 
```
#### How to merge branches

to merge a branch, lets say i want to merge branch_name with main,
```
git checkout main ; git merge branch_name
```
**Note:** checkout is deprecated from Git version 2.23 onwards so use switch instead

### Git rebase
The second way of combining work between branches is rebasing. Rebasing essentially takes a set of commits, "copies" them, and plops them down somewhere else.
While this sounds confusing, the advantage of rebasing is that it can be used to make a nice linear sequence of commits. The commit log / history of the repository will be a lot cleaner if only rebasing is allowed.

Lets say our commit tree looks like 
```
c0 -> c1 -> c3 (main)
	   L-> c2 (bug fix)
```
The following:
```
$ git checkout -b bugFix
$ git commit
$ git checkout main
$ git commit
$ git checkout bugFix
$ git rebase main
```
will produce:
```
c0 -> c1 -> c3 (main) -> c2' (bug fix)
```

### What is .gitignore
The .gitignore file is a text file that tells Git which files or folders to ignore in a project. A local . gitignore file is usually placed in the root directory of a project. You can also create a global . gitignore file and any entries in that file will be ignored in all of your Git repositories.

#### Format patterns of .gitignore
`*.c` ignores all .c files
'foo\[01\].txt' ignores the file literally named foo[01].txt
`*` ignores everything
`!/*.c` do not ignore .c files
`!/main.h` does not ignore file literally named main.h

### Extra commands
To create a shortcut for a Git command:
```
git config --global alias.<alias-name> <git-command>
```
eg.
```
git config --global alias.st status 
git config --global alias.co checkout 
git config --global alias.br branch 
git config --global alias.up rebase 
git config --global alias.ci commit 
```



