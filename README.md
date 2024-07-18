# Lab2 Git
## 1. create new project on local and push it to the remote repo
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

## 3. Merge Changes into the main Branch and Push
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


