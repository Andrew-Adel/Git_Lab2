# Lab2 Git Part 1
## 1. create new project on local and push it to the remote repo
![Screenshot from 2024-07-17 23-27-48](https://github.com/user-attachments/assets/ea1e2539-f186-418d-b9f8-ddaee2e8c9ba)
![Screenshot from 2024-07-18 00-29-31](https://github.com/user-attachments/assets/b1477c36-ca50-4d7d-be5a-9b8bf7700786)
```javascript
mkdir myproject
cd myproject
git init

echo "# Lab2 Git" >> README.md
git add README.md
git commit -m "Initial commit"

// create SSH key
 ssh-keygen -t ed25519 -C "andrew#########@gmail.com"

git remote add origin git@github.com:andrew/Git_Lab2.git

git push -u origin master
```
## 2. Create dev and test Branches, Create Files in dev Branch, and Push Changes
```javascript
git checkout -b dev

echo "This is file1, Created By Andrew Adel" >> file1.txt
echo "This is file2 Created By Andrew Adel" >> file2.txt
git add file1.txt file2.txt
git commit -m "Add file1 and file2 in dev branch"
git push -u origin dev

git branch --show-current
git switch master
git checkout -b test
git push -u origin test

```

![image](https://github.com/user-attachments/assets/17fcdd16-6424-4eba-a42f-3deffc04c618)
![image](https://github.com/user-attachments/assets/e4f1ebd2-2714-49ba-b9a6-1a7ede81d49c)

## 3. Merge Changes into the master Branch and Push
```javascript
git checkout master
git merge dev
git push -u origin master
```
![image](https://github.com/user-attachments/assets/727442e5-3e86-4d6f-bd33-0fd89513db0a)

## 4. Remove Branches Locally and Remotely
```javascript
git branch -d dev
git branch -d test

git push origin --delete dev
git push origin --delete test

restore the branches
git reflog
git checkout -b dev 5b2d569
git checkout -b test 0e89d62
 
```
![image](https://github.com/user-attachments/assets/97ff5435-8d1d-42fd-a073-56845dff4679)


# Lab2 Git Part 1
## 1. Create an annoted tag with tagnamr v1.4
```javascript
git tag -a v1.4 -m "Version 1.4"
```
## 2. Push the Tag to the Remote Server
```javascript
git push origin v1.4
```
## 3. List Tags Locally
```javascript
git tag
```
## 4. Delete Tag Locally and Globally
```javascript
//locally
git tag -d v1.4
//globally
git push origin --delete tag v1.4
```
## 5. What is Git Rebase? (With Example)
Git rebase is a way to integrate changes from one branch into another. It moves or "replays" the commits from one branch onto another, creating a linear project history.
```
A---B---C master
     \
      D---E feature
```
If you rebase feature onto master:
```
git checkout feature
git rebase master

```
it will act as 
```
A---B---C---D'---E' feature
```
it is look like if D and E is commit after last update of master as if created and add after C update

## 6. Pull Request
A pull request is a way to request that another developer reviews and merges your changes into a branch of a repository. This is commonly used in collaborative projects to ensure code quality and manage contributions.

### Steps to create a pull request:

1. Push your branch to the remote repository:
```
git push origin dev
```
2. Navigate to the repository on GitHub (or your Git hosting service).
3. Click the "Pull requests" tab.
4. Click the "New pull request" button.
5. Select the branch you want to merge into (e.g., main) and the branch you want to merge from (e.g., feature-branch).
6. Add a title and description for your pull request.
7. Click "Create pull request".

## 7. Add Image to README.md 
```javascript
![Alt text](URL_to_image)
![My Project Logo](https://example.com/my_project_logo.png)
```

## difference between clone, fetch, pull
### 1. Clone 
#### Command: 
```javascript 
git clone <repository-url>
```
#### Purpose: 
* Clones a repository from a remote server (like GitHub, GitLab, etc.) to your local machine.

#### Functionality:
* Copies the entire repository, including all branches, commits, and history.
* Sets up a local working copy of the repository.
* Initializes a remote tracking branch (origin/master, origin/dev, etc.) that corresponds to the default branch (master or main) on the remote repository.

#### Typical Usage: 
* Used to initially download a repository from a remote server to start working on it locally.

### 2. Fetch
#### Command: 
```javascript
git fetch [<remote>]
```
#### Purpose: 
* Fetches changes from a remote repository to your local repository without merging them.

#### Functionality:
* Downloads new data (commits, branches, tags) from a remote repository.
* Updates the remote tracking branches (origin/master, origin/dev, etc.) to reflect the latest changes on the remote, but does not integrate those changes into your local branches.

#### Typical Usage: 
* Used to see what changes are available from a remote repository before deciding to merge or pull them into your local branch.


### 3. Pull
#### Command: 
```javascript 
git pull [<remote>] [<branch>]
```

#### Purpose: 
* Fetches changes from a remote repository and merges them into your current branch.

#### Functionality:
* Performs a git fetch to retrieve the latest changes from the remote repository.
* Automatically merges the retrieved changes into the current branch (by default, this is the branch you are currently on).
* Combines git fetch and git merge in a single command.

#### Typical Usage: 
* Used to update your current branch with the latest changes from a remote repository. It is effectively git fetch followed by git merge.

### Key Differences

* Clone: Downloads an entire repository from a remote server to your local machine, including all branches and history.

* Fetch: Downloads new commits, branches, and tags from a remote repository to your local repository. It updates the remote tracking branches but does not integrate these changes into your working directory.

* Pull: Downloads new commits from a remote repository and integrates (merges) them into your current working branch. It effectively combines fetch and merge.
