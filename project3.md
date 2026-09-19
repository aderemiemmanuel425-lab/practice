[ COMPLETE MASTER COURSEWARE ]

Git & GitHub
Lecture Materials

■ Fundamentals & Local Workflows ■ Branching, Merging & Conflicts ■ GitHub Collaboration & Pull Requests

Press Next or Scroll to navigate slides

Title Slide

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 1]
1. Introduction to Git and GitHub

What is Git?
Git is a distributed version control system used to track changes in files and source
great.
✓ Track changes
✓ Save different versions of a project
✓ Work on features without affecting the main code
✓ Collaborate with other developers
✓ Revert unwanted changes
✓ Create branches
✓ Merge different pieces of work

What is GitHub?
GitHub is a cloud-based platform for hosting Git repositories and collaborating on
software projects.
Git = the tool that manages your code history locally GitHub = an online platform where Git
repositories can be stored and shared
Other Git hosting platforms include: GitLab and Bitbucket.

Slide 1 of 41

Slide 1 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 2]
2. Git vs GitHub

Git GitHub
Version control system Hosting/collaboration platform
Runs on your computer Runs primarily online
Tracks code changes Hosts Git repositories
Works without internet Usually requires internet
Uses commands like git commit Provides Pull Requests, Issues, etc.
Created for version control Provides collaboration features

Slide 2 of 41

Slide 2 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 3]
3. Why Do We Need Version Control?

Imagine you have:
● ● ● project structure
project/
+-- index.html
+-- style.css
+-- script.js
You modify script.js.
Later, you discover that the new code broke the application.
Without version control, you may struggle to recover the previous version.

With Git, you can look at your history:
Version 1 -> Version 2 -> Version 3 -> Version 4
Safe Recovery: You can return to an earlier version when necessary.

Slide 3 of 41

Slide 3 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 4]
4. Installing Git

Check whether Git is installed:
● ● ● bash
git --version
Example Output:
● ● ● output
git version 2.54.0

Linux Installation
For Arch Linux:
● ● ● pacman
sudo pacman -S git
For Ubuntu/Debian:
● ● ● apt
sudo apt install git

Slide 4 of 41

Slide 4 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 5]
5. Git Configuration

Before using Git, configure your identity.
Set username:
● ● ● bash
git config --global user.name "Your Name"
Set email:
● ● ● bash
git config --global user.email "you@example.com"

Check configuration:
● ● ● bash
git config --global --list
Or check individually:
● ● ● bash
git config user.name
git config user.email
Important The email you configure should normally correspond to an email associated with your
GitHub account if you want your commits properly associated with your GitHub profile.

Slide 5 of 41

Slide 5 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 6]
6. Understanding a Git Repository

A repository, or repo, is a project that Git is tracking.
Create a project:
● ● ● bash
mkdir git-demo
cd git-demo
Initialize Git:
● ● ● bash
git init
You should see something similar to:
● ● ● output
Initialized empty Git repository

The Hidden .git/ Directory
Git creates a hidden directory:
● ● ● terminal
.git/
This directory contains Git's internal information.
Check with:
● ● ● bash
ls -la

Never manually edit or delete the .git/ folder unless you want to un-initialize Git tracking for that
project!

Slide 6 of 41

Slide 6 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 7]
7. The Git Workflow

One of the most important concepts to understand is:
Working Directory
|
git add
|
Staging Area
|
git commit
|
Local Repository
|
git push
|
GitHub

Three Important Areas
Working Directory
Where you actually create and modify files.
Staging Area
Files you have selected to be included in the next commit.
Repository
The location where Git stores committed versions of your project.

Slide 7 of 41

Slide 7 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 8]
8. Checking the Status

Create a file:
● ● ● bash
touch index.html
Check Git:
● ● ● bash
git status

You may see:
● ● ● git status output
Untracked files:
index.html

Git knows the file exists, but it is not yet tracking it.

Slide 8 of 41

Slide 8 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 9]
9. Adding Files

Staging Changes
Add one file:
● ● ● bash
git add index.html
Or add everything:
● ● ● bash
git add .

Check status after staging:
● ● ● bash
git status
The file should now appear under:
● ● ● terminal
Changes to be committed
The file is now in the Staging Area, prepared for the next commit snapshot.

Slide 9 of 41

Slide 9 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 10]
10. Making a Commit

A commit is a saved snapshot of your project.
● ● ● bash
git commit -m "Initial commit"
Good commit messages describe what changed clearly and concisely.

Commit Message Examples
Good Examples:
✓ ✓ git commit -m "Add login form"
✓ ✓ git commit -m "Fix user authentication"
✓ ✓ git commit -m "Add product API"
Avoid vague messages such as:
✗ ✗ git commit -m "changes"
✗ ✗ git commit -m "stuff"

Slide 10 of 41

Slide 10 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 11]
11. Viewing Commit History

Log Commands
Use standard log:
● ● ● bash
git log
A shorter version:
● ● ● bash
git log --oneline

Example History Output
● ● ● git log --oneline
a82f91d Add login form
72bc432 Add homepage
19af234 Initial commit
Each line contains the unique short commit hash (e.g. a82f91d) followed by the commit message.
Slide 11 of 41

Slide 11 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 12]
12. Understanding the Basic Git Cycle

Students should practice this repeatedly:
● ● ● terminal workflow
# Create/modify files
git status
git add .
git status
git commit -m "Describe the change"
git log --oneline

The Core Rhythm
Modify -> Status -> Add -> Commit
Repeating this simple 4-step loop builds solid muscle memory for all Git development.

Slide 12 of 41

Slide 12 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 13]
13. Creating a GitHub Account

Go to github.com and follow these initial setup steps:
1. Create an account on GitHub.
2. Verify your email address.
3. Set a username (professional & memorable).
4. Configure your profile (bio, photo, links).
5. Create your first repository to test the connection.
Make sure the email used on GitHub matches the email configured in git config --global user.email.

Slide 13 of 41

Slide 13 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 14]
14. Creating a GitHub Repository

On GitHub:
1. Click New repository (or the + icon).
2. Enter the repository name.
3. Add a description if needed.
4. Choose Public or Private.
5. Click Create repository.

Example Repository Name
● ● ● Repo Name
git-demo
When creating a repository to push an existing local project into, leave "Initialize with README"
unchecked to avoid branch conflicts.

Slide 14 of 41

Slide 14 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 15]
15. Connecting Local Git to GitHub

After creating the GitHub repository, connect your local repository.
● ● ● bash
git remote add origin https://github.com/USERNAME/git-demo.git

Check the Remote:
● ● ● bash
git remote -v
You should see:
● ● ● terminal
origin https://github.com/USERNAME/git-demo.git (fetch)
origin https://github.com/USERNAME/git-demo.git (push)

Slide 15 of 41

Slide 15 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 16]
16. Understanding origin

origin is the conventional name given to the remote repository.
● ● ● example
git remote add origin https://github.com/USERNAME/project.git
This command means: "Create a remote alias called origin that points to this GitHub repository."

Slide 16 of 41

Slide 16 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 17]
17. Pushing Code to GitHub

First, make sure you have at least one commit in your local repository.
Then perform the initial push:
● ● ● bash (first push)
git push -u origin main
The -u flag (upstream) establishes tracking between your local main branch and origin/main.

Subsequent Pushes
After the initial upstream relationship is established, you can simply run:
● ● ● bash (subsequent)
git push
Git will automatically push new commits to the tracked upstream branch on GitHub.

Slide 17 of 41

Slide 17 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 18]
18. main vs master

Modern GitHub repositories commonly use main as the default branch.
Check your current branch:
● ● ● bash
git branch

Renaming to main
Rename the current branch to main:
● ● ● bash
git branch -M main
Then push to origin:
● ● ● bash
git push -u origin main

Slide 18 of 41

Slide 18 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 19]
19. Cloning a Repository

Clone means downloading an existing Git repository to your computer.
● ● ● bash
git clone https://github.com/USERNAME/project.git
cd project
git status
Cloning automatically sets up origin and checks out the default branch ready for work.

Slide 19 of 41

Slide 19 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 20]
20. git pull

git pull downloads changes from the remote repository and integrates them into your
local branch.
● ● ● bash
git pull
Best Practice: Use it before starting work when other team members may have pushed changes.

Typical Workflow
GitHub
|
git pull
|
Local repository

Slide 20 of 41

Slide 20 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 21]
21. git fetch

git fetch downloads information about changes from the remote repository without
immediately merging them into your current branch.
● ● ● bash
git fetch

Key Difference
git fetch -> download remote changes
git pull -> fetch + integrate changes
git pull is essentially git fetch followed immediately by git merge.

Slide 21 of 41

Slide 21 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 22]
22. Git Branches

A branch allows you to work on a separate version of your project.
View branches:
● ● ● bash
git branch
Create a branch:
● ● ● bash
git branch feature-login

Switching Branches
Switch to it:
● ● ● bash
git switch feature-login
Or create and switch at the same time:
● ● ● bash
git switch -c feature-login

Slide 22 of 41

Slide 22 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 23]
23. Why Use Branches?

Imagine your application has: main
A developer wants to create a login system.
Instead of modifying main directly, they branch off:
main
|
+-- feature-login

Isolated Development
The developer works on feature-login without disturbing the main application.
Team members can test, experiment, and deploy other fixes on main safely while the feature is in
progress.

Slide 23 of 41

Slide 23 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 24]
24. Merging Branches

After completing the feature:
1. Switch back to main:
● ● ● bash
git switch main
2. Merge the feature branch:
● ● ● bash
git merge feature-login

Integration
The changes from feature-login are merged into main.
main ---------* (merged)
| ^
+---*------+ (feature-login)

Slide 24 of 41

Slide 24 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 25]
25. Deleting a Branch

Local Branch Deletion
After merging, delete the local branch to keep your repository tidy:
● ● ● bash
git branch -d feature-login

Remote Branch Deletion
To delete a remote branch from GitHub:
● ● ● bash
git push origin --delete feature-login
Deleting merged feature branches prevents clutter in your repository's branch list.

Slide 25 of 41

Slide 25 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 26]
26. GitHub Pull Requests

A Pull Request (PR) is a request to merge changes from one branch into another.
For team projects, this is one of the most important GitHub workflows.
Pull requests allow teammates to review code, suggest revisions, run automated tests (CI), and
discuss implementations before merging into production.

Typical Workflow Pipeline
Create branch
|
Write code
|
Commit
|
Push branch
|
Create Pull Request
|
Code Review
|
Approval
|
Merge

Slide 26 of 41

Slide 26 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 27]
27. Pull Request Example

Suppose main is the production branch.
You create feature-payment.
After completing the feature:
● ● ● bash
git add .
git commit -m "Add payment integration"
git push -u origin feature-payment

Create PR on GitHub
Go to GitHub and create a Pull Request:
● ● ● terminal
feature-payment -> main
Your teammates can review the code before it is merged into production.

Slide 27 of 41

Slide 27 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 28]
28. Git Merge Conflicts

What is a Conflict?
A conflict happens when Git cannot automatically determine which change should be kept.
Developer A:
● ● ● terminal
const name = "John";
Developer B:
● ● ● terminal
const name = "David";
Both modify the same line!

Git Conflict Markers
<<<<<<< HEAD
const name = "John";
=======
const name = "David";
>>>>>>> feature-name
You must manually decide which version to keep.
● ● ● resolve and commit
git add .
git commit -m "Resolve merge conflict"

Slide 28 of 41

Slide 28 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 29]
29. .gitignore

.gitignore tells Git which files should not be tracked.
For a Node.js project:
● ● ● .gitignore example
node_modules/
.env
dist/
coverage/
Create file:
● ● ● bash
touch .gitignore

Why .gitignore Matters
Never commit sensitive information such as:
✓ .env
✓ passwords
✓ API keys
✓ private credentials
Once pushed to GitHub, sensitive keys can be indexed within seconds by automated bots.

Slide 29 of 41

Slide 29 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 30]
30. Git Diff

Review Unstaged Changes
See changes that have not been staged:
● ● ● bash
git diff

Review Staged Changes
See staged changes:
● ● ● bash
git diff --staged
This helps you review your work before committing to maintain clean and deliberate git history.

Slide 30 of 41

Slide 30 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 31]
31. Undoing Changes

Unstage a file
Remove file from staging without losing modifications:
● ● ● bash
git restore --staged filename

Discard changes in a file
Revert working directory file to last committed state:
● ● ● bash
git restore filename
Be careful: this can permanently remove uncommitted changes.

Slide 31 of 41

Slide 31 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 32]
32. Reverting a Commit

If a commit has already been shared, a safer approach is often:
● ● ● bash
git revert <commit-id>
Git creates a new commit that reverses the earlier commit.

This is generally safer for shared branches than rewriting history, because it preserves existing commits for collaborators.

Slide 32 of 41

Slide 32 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 33]
33. Git Reset

Git reset can move the current branch pointer and, depending on the option, change
the staging area or working tree.
● ● ● git reset options
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1

Warning
Be especially careful with: git reset --hard because uncommitted work can be permanently lost.

Slide 33 of 41

Slide 33 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 34]
34. GitHub Issues

GitHub Issues can be used to track:
✓ Bugs
✓ Features
✓ Tasks
✓ Improvements
✓ Questions

Example Issue
● ● ● Issue #12
Issue #12
Title: Fix login validation
Description:
The login form accepts empty passwords.
Expected:
Password should be required.

Slide 34 of 41

Slide 34 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 35]
35. GitHub README

A README.md explains the project.
A good README can contain:
✓ Project name
✓ Description
✓ Features
✓ Technologies
✓ Installation
✓ Usage
✓ API documentation
✓ Contributing
✓ License

Example README.md
● ● ● README.md
# My Project
A simple backend API built with NestJS.
## Installation
npm install
## Running the application
npm run start:dev

Slide 35 of 41

Slide 35 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 36]
36. Forking

A fork creates your own GitHub copy of another person's repository.
Forking is the bedrock of open-source software collaboration across the world.

Typical Open-Source Workflow
Original Repository
|
Fork
|
Your GitHub Repository
|
Clone
|
Make changes
|
Push
|
Pull Request

Slide 36 of 41

Slide 36 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 37]
37. Git Tags

Tags are used to mark important points in project history, commonly releases.
Create a tag:
● ● ● bash
git tag v1.0.0

Push it to GitHub:
● ● ● bash
git push origin v1.0.0
List tags:
● ● ● bash
git tag

Slide 37 of 41

Slide 37 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 38]
38. Useful Git Commands

git init — Initialize repository git status — Show repository status
git add — Stage changes git commit — Save changes
git log — View history git clone — Copy repository
git push — Upload changes git pull — Download & integrate changes
git fetch — Download remote info git branch — Manage branches
git switch — Change branches git merge — Merge branches
git diff — View changes git restore — Restore files
git revert — Reverse a commit git remote — Manage remote repositories
git tag — Create / list release tags

Slide 38 of 41

Slide 38 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 39]
39. Recommended Teaching Procedure

Class 1: Fundamentals
Theory:
✓ Version control
✓ Git vs GitHub
✓ Working dir & Index
Practical:
● ● ● terminal
git init
git add .
git commit

Class 2: GitHub
Teach:
✓ GitHub account & repo
✓ Remote & origin
✓ Push, Clone, Pull
Practical:
● ● ● terminal
git remote add
git push -u origin

Class 3: Branching
Teach:
✓ Why branches matter
✓ Creating & switching
✓ Merging & deletion
Practical:
● ● ● terminal
git switch -c feat
git merge feat

Class 4: Team Collab
Teach:
✓ Pull Requests & Reviews
✓ Merge conflicts
✓ .gitignore & Forks
Pair work:
● ● ● terminal
Student A -> login
Student B -> register

Class 5: Advanced Git
Teach:
✓ git fetch & diff
✓ restore, revert, reset
✓ Tags & Aliases
✓ Good commit messages

Slide 39 of 41

Slide 39 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 40]
40. Final Practical Project

Student Management System
Each student should execute these 15 steps:
1. Create a project.
2. Initialize Git.
3. Create GitHub repository.
4. Add a README.
5. Create .gitignore.
6. Make an initial commit.
7. Push to GitHub.
8. Create feature-student branch.
9. Add a feature.
10. Commit the feature.
11. Push the branch.
12. Create a Pull Request.
13. Review the Pull Request.
14. Merge it into main.
15. Delete feature branch.

Team Workflow Architecture
main

|

+----------+----------+
| |
feature-login feature-register
| |
| |
commit commit
| |
| |
push push
| |
+----------+----------+

|
Pull Requests
|
Review
|
Merge
|
main

Slide 40 of 41

Slide 40 of 41

Git & GitHub — Lecture Materials

Git & GitHub • Interactive Master Courseware
[SECTION 41]
41. Key Rules for Students

Basic Individual Workflow
CHANGE
|
git status
|
git add .
|
git commit -m "message"
|
git push

Team Workflow
git pull
|
Create branch
|
Write code
|
git add
|
git commit
|
git push
|
Pull Request
|
Review
