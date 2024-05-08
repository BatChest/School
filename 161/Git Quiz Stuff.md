# Interactive Rebase
- **Git Interactive Rebase** allows you to modify your commit history in many ways. 
	- It provides an interface where you can decide what should happen with each commit. 
	- You can squash commits together, split them apart, reorder them, and even change their messages.

Here’s how you can use it:

1. **Start an Interactive Rebase:** To start an interactive rebase, you use the command `git rebase -i`, followed by the commit or branch you want to rebase onto. For example, if you want to rebase onto the `HEAD~5` (the fifth last commit), you would use `git rebase -i HEAD~5`.
    
2. **Choose Actions for Each Commit:** This will open a text editor with a list of all the commits between the current `HEAD` and the one you’re rebasing onto. Each line represents a commit and starts with the word `pick`. You can replace `pick` with the action you want to take:
    - `pick`: use the commit as is.
    - `reword`: use the commit but edit the commit message.
    - `edit`: use the commit but stop for amending.
    - `squash`: use the commit but meld into the previous commit.
    - `fixup`: like `squash`, but discard this commit’s log message.
    - `drop`: remove the commit.
3. **Save and Exit:** Once you’ve chosen your actions, save and close the editor. Git will then start applying the commits with the actions you chose.
    
4. **Resolve Conflicts (if any):** If there are any conflicts between the commits, Git will pause and allow you to resolve those conflicts before continuing. Once you’ve resolved the conflicts, you can continue the rebase with `git rebase --continue`.
    
5. **Abort if Necessary:** If at any point you want to stop the rebase and go back to where you were, you can use `git rebase --abort`.

# Bisect
**Git Bisect** is a powerful tool used for debugging in Git. It uses a binary search algorithm to find which commit in your project’s history introduced a bug. Checks the changes from one commit

1. **Start the Bisect Process:** To start the bisect process, you use the command `git bisect start`.
2. **Mark the Bad Commit:** Next, you need to tell Git which commit is bad, meaning it’s known to contain the bug. This is usually your current commit (`HEAD`). You can do this with `git bisect bad`.
3. **Mark the Good Commit:** Then, you need to tell Git about a commit that is good, meaning it’s known to be free of the bug. This could be an earlier commit where you know the bug did not exist. You can do this with `git bisect good <commit>`.
4. **Bisecting:** Git will now checkout a commit midway between the good and bad commits. Test this commit for the bug. If the bug is present, type `git bisect bad`. If it’s not, type `git bisect good`. Git will continue to narrow down the range of commits until it identifies the exact commit that introduced the bug.
5. **End the Bisect Process:** Once you’ve found the offending commit, you can end the bisect process with `git bisect reset`. This will return your HEAD to where it was before the bisect process.

# Version Control
**Version Control**, also known as source control, is a system that records changes to a file or set of files over time so that you can recall specific versions later. It allows you to:

- **Revert** files back to a previous state.
- **Revert** the entire project back to a previous state.
- **Compare** changes over time.
- **See** who last modified something that might be causing a problem.
- **See** who introduced an issue and when.

Now, when we say a Version Control System (VCS) is **distributed**, like Git, it means that the complete codebase and history is mirrored on every developer’s computer. This is different from a centralized version control system, like SVN, where there is a single, central copy of your project on a server and developers get only a snapshot of the files they’re working on.

In a **distributed VCS**:
- Every clone is a full backup of all the data.
- You can work offline or without access to the central server.
- You can use several workflows including solo, team, and collaborative.
- Operations (like commits, viewing history, and reverting changes) are faster because there’s no need to communicate with a central server.

# Basic elements of VCS
1. **Repository:** This is the .git/ folder in your project. It tracks all changes made to files in your project, building a history over time.
    
2. **Remote:** This is a version of your project that is hosted on the internet or network somewhere. You can have several of these, each of which can be read from or written to.
    
3. **Staging Area:** Also known as the “index”, this is an intermediate area where commits can be formatted and reviewed before completing the commit.
    
4. **Changes:** Changes are the differences in content from one commit to another, or between the repository and the working directory.
    
5. **Diffs:** A ‘diff’ is the output from the git diff command showing the changes between commits, commit and working tree, etc.
    
6. **Branches:** A branch is a parallel version of a repository. It is contained within the repository, but does not affect the primary or master branch allowing you to work freely without disrupting the “live” version. When you’ve made the changes you want to make, you can merge your branch back into the master branch to publish your changes.
    
7. **Commits:** A commit, or “revision”, is an individual change to a file (or set of files). It’s like when you save a file, except with Git, every time you save it creates a unique ID (a.k.a. the “SHA” or “hash”) that allows you to keep record of what changes were made when and by who. Commits usually contain a commit message which is a brief description of what changes were made.
    
8. **Working Directory:** The Working Directory is the files that you see in your computer’s file system. When you open your project files into a text editor, you’re working with files in the Working Directory.
    
9. **Checkout:** When content is checked out, it is taken from the repository and placed in your working directory.
   
10. **push**: is a command that is used to upload local repository content to a remote repository. After you’ve made changes to your local repository and committed those changes, you can use `git push` to share these changes with the remote repository.


# Git Workflow
## Basic Git Workflow
![[Pasted image 20240507160650.png]]
- **Modify:** Files in your working directory
- **Stages:** files, adding snapshots of them to your staging area
- **Commit** which takes the files in the staging area and stores that snapshot permanently to your Git directory 

## Git Workflow
1. **Making Changes:** This is where you modify files in your working directory.
    
2. **Adding Changes:** Once you’ve made changes, you need to add them to the staging area. You can do this with the `git add` command. For example, `git add .` adds all changes in the current directory, and `git add <file>` adds changes in a specific file.
    
3. **Committing:** After adding your changes to the staging area, you can commit them to your local repository with the `git commit` command. For example, `git commit -m "Your commit message"` will commit your changes with a descriptive message.
    
4. **Pushing:** Once your changes are committed locally, you can push them to a remote repository with the `git push` command. For example, `git push origin master` will push your changes to the master branch of the origin remote.
    
5. **Pulling:** If others have made changes to the remote repository, you can pull those changes to your local repository with the `git pull` command. For example, `git pull origin master` will pull changes from the master branch of the origin remote.
    
6. **Branching:** You can create a new branch in your repository with the `git branch` command. For example, `git branch new-feature` will create a new branch called “new-feature”. You can switch to this branch with `git checkout new-feature`.
    
7. **Merging:** After making changes on a branch, you can merge those changes into another branch (like master) with the `git merge` command. For example, if you’re currently on the master branch, you can merge the new-feature branch into master with `git merge new-feature`.
    
8. **Rebasing:** Rebasing is another way to integrate changes from one branch into another. It’s a bit more complex than merging, but it can make your commit history cleaner. You can start a rebase with the `git rebase` command. For example, `git rebase master` will rebase your current branch onto master.

## Example Workflow
![Pasted image 20240507162152](https://github.com/BatChest/School/assets/90287766/928336e6-f773-41f5-a0f8-18bce410917d)

## Merge conflict
A **merge conflict** occurs when Git is unable to automatically resolve differences in code between two commits. When all the changes in the code occur on different lines or in different files, Git will successfully merge commits without your help. But if there are conflicting changes on the same line or in the same file, Git will need your help to decide which changes to incorporate.

Here’s a step-by-step guide on how merge conflicts happen:

1. You `git pull` the latest changes from a remote repository.
2. You start working on this code and make some changes.
3. In the meantime, someone else also modifies the same lines in the same file in the remote repository.
4. They push their changes to the remote repository.
5. You attempt to `git pull` again or `git merge` another branch into your current branch.

At this point, Git doesn’t know which changes to use - yours or the other person’s. This is a merge conflict.

To resolve a merge conflict, you have to manually edit the conflicted file to select which changes you want to keep. Git will mark the areas in your file where conflicts occurred with conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`). You can search your file for these markers and decide which changes to keep.

After you’ve resolved all conflicts, you can run `git add` to stage the resolved files, and then `git commit` to commit the resolution of the merge conflict.


# Collaboration using Git
## Collaborative workflows

1. **GitFlow** is a branching model for Git, created by Vincent Driessen. It’s a solution for managing features, releases, and hotfixes within your projects. Here’s how it works:
    
    - It has two main branches: `master` and `develop`. The `master` branch stores the official release history, and the `develop` branch serves as an integration branch for features.
    - Each new feature resides in its own branch, which can be pushed to the `develop` branch for testing.
    - When the feature is fully tested, it gets merged into `develop`.
    - To start a release, you create a release branch off of `develop`.
    - Once the release is ready to ship, it gets merged into `master` and `develop`, then the release branch is deleted.
    - If a critical issue that needs to be fixed right away pops up, you would create a hotfix branch off of `master`, make the fix, then merge it back into both `master` and `develop`.

1. **Trunk-Based Development** is a source-control branching model where developers work on a single branch called ‘trunk’ (`master` in Git), resist any pressure to create other long-lived development branches by employing documented techniques. They therefore avoid merge hell, do not break the build, and live happily ever after. Here’s how it works:
    
    - All developers work on a single branch with complete/unabridged history (`master`).
    - Developers pull changes from `master` frequently (at least daily).
    - Developers push to `master` frequently (once their changes are ready and pass all tests).
    - Branches are short-lived and regularly merged back into `master` (feature branches should usually exist for less than a day before they are merged back in).
    - Releases are simply a specific commit on `master` that is tagged with a version number.

# Basic concepts in development
- **Issue/Ticket**: a post that captures a problem with existing software, or a request for a new functionality
- **Feature:** A new functionality or enhancement added to a software product
- **Release:** A version of a software product made available for distribution and deployment
- **Hotfix:** A quick fix or patch to address a critical bug or issue in a released software product
	- "prod" uction: released software
- **Pull request:** A request to merge changes from one branch to another in a version control system
![Pasted image 20240505161150](https://github.com/BatChest/School/assets/90287766/ff7fdd2e-9ace-4c86-b3ab-18f5ef3b2416)

# Software development models
- **Waterfall**
	- Linear sequential model with distinct phases
	- Each phase must be completed before moving to the next 
- **Kanban**
	- Visual workflow management using boards and cards 
	- Focuses on continuous delivery and limiting work in progress 
- **Scrum**
	- Iterative and incremental approach with time-boxed sprints 
	- Emphasizes collaboration, flexibility, and delivery working software 
- **Agile**
	- Umbrella term for iterative and adaptive development methodologies
	- Values individuals, interactions, working software, and customer collaboration
- **XP (Extreme Programming)**
	- Agile methodology focusing on software quality and responsiveness to change
	- Practices include pair programming, continuous integration, and test-driven development  

# What's common?
- **Shared mental mode:** to reduce cognitive load 
- Each attempt to deliver a **set of compatible rituals and tools** to handle various steps in the code development process 

# Steps in the development process
- Writing new software ("**features**")
	- **Development:** Developers work on new features or bug fixes in their own branches.
	- **Staging:** Changes are staged using `git add`, then committed using `git commit`.
- Checking that the software is correct (**code review**)
	- Before changes are merged into the main codebase, they are often reviewed by other developers. This can be done through a Pull Request on platforms like GitHub.
	- Changes are tested to ensure they work as expected and don’t introduce new bugs. This can involve unit tests, integration tests, and manual testing.
- Combining new and old functionality (**pull request, merge**)
- Delivering new functionality to users of the software (**release**)
	- Once changes have been reviewed and tested, they are merged into the main codebase and deployed to production.


## Commands Used:
1. **git clone:** This command is used to create a copy of a remote repository on your local machine.
    
2. **git branch:** This command is used to create a new branch in your repository. It’s common to create a new branch for each new feature or bug fix.
    
3. **git checkout:** This command is used to switch between branches in your repository.
    
4. **git pull:** This command is used to fetch the latest changes from the remote repository and merge them into your current branch.
    
5. **git add:** This command is used to stage changes for commit. You can add individual files, or all changes in your repository.
    
6. **git commit:** This command is used to save your changes to the local repository. Each commit has a message associated with it which describes the changes made.
    
7. **git push:** This command is used to upload your local repository changes to the remote repository.
    
8. **git merge:** This command is used to combine changes from one branch into another. You might do this when a feature is complete and ready to be included in the main code.
    
9. **git rebase:** This command is used to move or combine a sequence of commits to a new base commit. It’s an alternative to `git merge`.

Gitflow
![Pasted image 20240505162323](https://github.com/BatChest/School/assets/90287766/c34aaf8d-3a34-4646-91b7-9cd317f8995b)

![Pasted image 20240505162416](https://github.com/BatChest/School/assets/90287766/fd8b7786-11a2-4dec-b0f3-35da81913217)
- **Integration:** We need to get each commit to play nice together before we release the software to users

- **Origin:** the name of remote usually points to GitHub

# Trunk-Based Development 
- Developers work on single branch, known as the "trunk" or "mainline"
- Short-lived feature branches are created off the trunk for each new feature or change
- Developers integrate their changes to the trunk frequently, at least daily
- Continuous integration ensures the trunk is always in a releasable state
- Release branches may be used for preparing releases 
- Promotes collaboration, reduces merge conflicts, and enables continuous delivery 
![Pasted image 20240505163201](https://github.com/BatChest/School/assets/90287766/7d985c98-685e-4767-aaa8-1210f051d1eb)


# Comparison
![Pasted image 20240505163236](https://github.com/BatChest/School/assets/90287766/15d609fa-3041-4884-b472-a6d5445dc998)
