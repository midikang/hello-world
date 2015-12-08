9: FIXING COMMON ISSUES WITH GIT
========
 
Creating a Repository on the Command Line
========
You'll only be working locally for this section, so you won't need to interact with GitHub. Thus, it's a good chance to learn how to use Git on the command line to create a new local repo.

On the next slide you'll learn how to use git init to create a local repository, and then we'll use that repo in the rest of this lesson.

Creating a Repository on the Command Line: Recap
========
To create a project from scratch, type git init <directoryname>.
This creates the directory as a subdirectory of the current location, and initializes a repo there.
You will have to create your README.md file manually.

Creating a Repository on the Command Line
========
1. Initialize a new git repository.
2. Create a README.md file and commit it to the repository.
3. Create and commit a file called badname.md. You will use this later.
4. Create a branch in your new repository.

git init
========
TEMPLATE DIRECTORY

The template directory contains files and directories that will be copied to the $GIT_DIR after it is created.

The template directory used will (in order):

The argument given with the --template option.

The contents of the $GIT_TEMPLATE_DIR environment variable.

The init.templatedir configuration variable.

The default template directory: /usr/share/git-core/templates.



EXAMPLES
========
Start a new Git repository for an existing code base
$ cd /path/to/my/codebase
$ git init      <1>
$ git add .     <2>
prepare /path/to/my/codebase/.git directory

add all existing file to the index

My steps
====
- mkdir midi-local-github
- git init midi-local-github/
  
  Initialized empty Git repository in d:/GitMidi/midi-local-github/.git/
  
  (use "git rm --cached <file>..." to unstage)
-  git rm --cached README.md
  
