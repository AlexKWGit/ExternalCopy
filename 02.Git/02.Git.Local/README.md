# Home task 02. Basic operation with Git.
Training in basic commands for working with Git.
  https://github.com/pluhin/sa.it-academy.by/wiki/02.-GIT.-Local

-----------------------------------------------------------------------------
## Task 1. Initializing a Local Repository.

Homework Assignment 1: Initializing a Local Repository
  1. Create a new directory on your local machine.
  2. Navigate to the newly created directory using the command line.
  3. Initialize a new Git repository in this directory.
  4. Create a new file named README.md and add some content to it.
  5. Stage and commit the README.md file to the repository.

�������� ������� 1. ������������� ���������� �����������
  1. �������� ����� ������� �� ����� ��������� ����������.
  2. ��������� �� ����� ��������� ������� � ������� ��������� ������.
  3. ��������������� ����� ����������� Git � ���� ��������.
  4. �������� ����� ���� � ������ README.md � �������� � ���� ����������.
  5. ����������� � ������������ README.md ���� � �����������.
-----------------------------------------------------------------------------
```bash
md 02.Git
cd 02.Git
git config --local user.name "Aleksandr Kuznecov"
git config --local user.email "AlexKWGit@gmail.com"
git init
echo Home task: 02.Git.local> README.md
git add README.md
git commit -m "Add first file in main branch"
```
-----------------------------------------------------------------------------
## Task 2. Basic Version Control.

Homework Assignment 2: Basic Version Control
  1. Create a new branch named feature-branch.
  2. Edit the README.md file to add a brief description of your project.
  3. Commit your changes to the feature-branch.
  4. Switch back to the main branch (usually master or main).
  5. Merge the changes from feature-branch into the main branch.

�������� ������� 2: ������� �������� ������
  1. �������� ����� ����� � ������ feature-branch.
  2. �������������� README.md ����, ������� ������� �������� ������ �������.
  3. ������������ ���� ��������� � ����� feature-branch.
  4. ��������� � �������� ����� (������ master ��� main).
  5. ���������� ��������� �� feature-branch �������� �����.
-----------------------------------------------------------------------------
```bash
git branch feature-branch
git checkout feature-branch
edit in editor "far": README.md
  // Add title symbol in first str.
  // Add str: Training in basic commands for working with Git.
git commit -am "Add in staged and commit with one command."
git checkout master
git merge feature-branch
```
Question:
Should I delete the "feature-branch" branch?
If you need to delete, then there is a command:
```bash
  git branch -d
```
-----------------------------------------------------------------------------
## Task 3. Exploring Git History.

Homework Assignment 3: Exploring Git History
  1. Use the git log command to view the commit history of your repository.
  2. Identify the commit hashes, dates, and commit messages.
  3. Try using different formatting options for git log to customize the output.
  4. Use git show <commit-hash> to view the details of a specific commit.

�������� ������� 3: �������� ������� Git
  1. ����������� git log ������� ��� ��������� ������� �������� ������ �����������.
  2. ���������� ����, ���� � ��������� ��������.
  3. ���������� ������������ ��������� ��������� �������������� ��� git log ��������� ������.
  4. ����������� git show <commit-hash> ��� ��������� �������� � ���������� �������.
-----------------------------------------------------------------------------
```bash
git log
git checkout feature-branch
git log
git checkout master
git log --oneline
git log -p
git log -1
git log -2
git log -p --oneline -2 ad8e63b
git show
git show ad8e63b38367f6501ae94964bdf454dcf8b5009d
git show ad8e63b
git show ad8e63b --oneline

// :) git log -p == git show

echo *.log>.gitignore
git add --all
git commit -m "Add file gitignore"
git status

edit: .gitignore
git commit -am "Add a new commit because there is not enough history for the test"
```
-----------------------------------------------------------------------------
## Task 4. Creating and Applying Tags.

Homework Assignment 4: Creating and Applying Tags
  1. Create a tag named v1.0 on a specific commit in your repository's history.
  2. Verify that the tag has been created successfully.
  3. Make some additional changes to the README.md file and commit them.
  4. Create a new tag named v2.0 on the latest commit.
  5. Explore the difference between annotated and lightweight tags.

�������� ������� 4: �������� � ���������� �����
  1. �������� ��� � ������ v1.0 ������������� ������� � ������� ������ �����������.
  2. ���������, ��� ��� ��� ������� ������.
  3. ������� � ���� �������������� ��������� README.md � ������������ ��.
  4. �������� ����� ��� � ������ v2.0���������� �������.
? 5. ������� ������� ����� ��������������� � ������������ ������.
-----------------------------------------------------------------------------
```bash
git log --oneline
git checkout ad8e63b
git log --oneline
git tag -a R1.0 -m "Release 1.0"
git checkout master
git tag -a R1.1 -m "Release 1.1"
git log --oneline
edit: README.md
git add --all
git commit -m "Changed for tag and release.
git tag -a R2.0 -m "Release 2.0"
git tag
git tag -l "R1*"
git tag  "R1*"
git checkout r1.1
git tag r1l
git tag
git checkout master
git log --oneline
git show r1l
git log --pretty=oneline
git tag TestTeg-1 10ec605
git tag -d r1l
```
-----------------------------------------------------------------------------
## Task 5. Undoing Changes.

Homework Assignment 5: Undoing Changes
  1. Create a new branch named bug-fix.
  2. Make a change to the README.md file and commit it.
  3. Make another change and commit it.
  4. Use git reset to undo the most recent commit while keeping the changes.
  5. Explore the effects of git reset with different options (soft, mixed, hard).

�������� ������� 5: ������ ���������
  1. �������� ����� ����� � ������ bug-fix.
  2. ������� ��������� � README.md ���� � ������������ ���.
  3. ������� ��� ���� ��������� � ������������ ���.
  4. ����������� git reset, ����� �������� ����� ��������� ��������, �������� ���������.
  5. ���������� ������� git reset � ���������� ���������� (������, ���������, �������).
-----------------------------------------------------------------------------
```bash
git branch
git checkout -b bug-fix
edit: README.md
git branch
git commit -m "Test commit."
git commit -am "Test commit."
git log --oneline
edit: README.md
git commit -am "Test 2 commit."
git reset --hard
git commit -am "Reset - Test 2 commit."
git reset --hard 063198e
git log --oneline
git reset --soft
edit: README.md
git commit -am "Recommit with changes after soft restore"
git status
git log --oneline
git reset --sort 063198e
git reset --soft 9089e00
git status
git add --all
git status
git commit -m "Recommit all changes"
// git commit --amend -a
// git reset --hard HARD~2

// git checkout master
// git merge bug-fix
```
-----------------------------------------------------------------------------
## Task 6. Stashing Changes.

Homework Assignment 6: Stashing Changes
  1. Create a new branch named experimental-feature.
  2. Make some changes to the README.md file but do not commit them.
  3. Use git stash to temporarily store your changes.
  4. Switch to another branch and make a different set of changes.
  5. Apply the changes from the stash to the experimental-feature branch.

�������� ������� 6: ���������� ���������
  1. �������� ����� ����� � ������ experimental-feature.
  2. ������� ��������� ��������� � README.md ����, �� �� ���������� ��.
  3. ����������� git stash ��� ���������� ���������� ���������.
  4. ������������� �� ������ ����� � ������� ������ ����� ���������.
  5. ��������� ��������� �� ������� � experimental-feature �����.
-----------------------------------------------------------------------------
```bash
git checkout master
git checkout -b experimental-feature
edit: README.md
git add --all
git stash push
git status
git stash list
git checkout bug-fix
git stash apply

git add --all
git commit -m "Commit changes that were received from stash."
git log --oneline
git reset e853b5a --hard
git log --oneline

git stash apply
edit: README.md // modify conflict
git add --all
git status
git commit -m "Commit changes that were received from stash."
git stash list
git stash drop
```
-----------------------------------------------------------------------------
## Task 7. Git Aliases and Configuration.

Homework Assignment 7: Git Aliases and Configuration
  1. Configure your Git username and email globally.
  2. Set up a custom alias for a frequently used Git command.
  3. Use the git config command to verify your configuration changes.

�������� ������� 7: ���������� � ������������ Git
  1. ��������� ���� ��� ������������ Git � ����� ����������� ����� �� ����� ����.
  2. ��������� ����������� ��������� ��� ����� ������������ ������� Git.
  3. ����������� git config �������, ����� ��������� ��������� ������������.
-----------------------------------------------------------------------------
```bash
git config --global user.name "Alexandr Kuznetsov"
git config --global user.email "AlexKWGit@gmail.com"

git config --global alias.lo 'log --oneline'
git lo
git config --global alias.co checkout
git config --global alias.br branch

git config --list

git revert --continue // �������� 
git revert <> // �������� 
```