# GIT AND GITHUB

    git status
  
**untracked files --> files in working directory**

**tracked files -->  files in staging area**

_use any command to add from working directory to staging area_

   git add file1
   git add .
   git add --all 

    git log      //tells the commit info on repository

fatal: your current branch 'master' does not have any commits yet

root@DESKTOP-HRRUJAL MINGW64 ~/Desktop/git (master)

     git commit -m "my first commit"

[master (root-commit) 1519369] my first commit

 1 file changed, 0 insertions(+), 0 deletions(-)
 
 create mode 100644 file1

root@DESKTOP-HRRUJAL MINGW64 ~/Desktop/git (master)
        
      git log
commit 1519369f9378c482686549c521440c069d2c4318 (HEAD -> master)
Author: krushnaji <rkrushnaji@gmail.com>
Date:   Tue Feb 16 15:44:39 2021 +0530

    my first commit

root@DESKTOP-HRRUJAL MINGW64 ~/Desktop/git (master)



    git diff   //compare changes of WD with staging area

    git diff --staged  //compare changes of staging area with local repo

    git diff HEAD  ///compare changes of WD with local repo

root@DESKTOP-HRRUJAL MINGW64 ~/Desktop/git (master)
$ git log
commit fb85d614993b0ae7fa6abc137498d9199d42afc4 (HEAD -> master)
Author: krushnaji <rkrushnaji@gmail.com>
Date:   Tue Feb 16 16:43:56 2021 +0530

    third commit

commit 0e37ec4bd4f00fc16151835a3187c3a317797ccf
Author: krushnaji <rkrushnaji@gmail.com>
Date:   Tue Feb 16 15:59:21 2021 +0530

    my second commit

commit 1519369f9378c482686549c521440c069d2c4318
Author: krushnaji <rkrushnaji@gmail.com>
Date:   Tue Feb 16 15:44:39 2021 +0530

    my first commit

root@DESKTOP-HRRUJAL MINGW64 ~/Desktop/git (master)
$ git diff fb85d614993b 1519369f9378c48
diff --git a/file1 b/file1
new file mode 100644
index 0000000..e69de29
diff --git a/file2 b/file2
deleted file mode 100644
index f138820..0000000
--- a/file2
+++ /dev/null     /////file not created at that time
@@ -1 +0,0 @@
-this is file2
diff --git a/file3 b/file3
deleted file mode 100644
index a309e46..0000000
--- a/file3
+++ /dev/null
@@ -1 +0,0 @@
-this is file3
diff --git a/file4 b/file4
deleted file mode 100644
index 1cb80c4..0000000
--- a/file4
+++ /dev/null
@@ -1 +0,0 @@
-this is file4

root@DESKTOP-HRRUJAL MINGW64 ~/Desktop/git (master)


    git clone   ///to clone the remote repo

if repository is not exist in local system then only we use git clone

    git pull

repository is already available but we need to fetch few changes only from remote repo

whatever changes (commits) are there in remove repository...same commits are not available in local repo then we use git pull


Unable to push changes onto remote repository


best practice is to use git pull before git push to match the commit id.
while working with multiple devlopers if commit id is diffrent than remote repo then the developer was Unable to push changes onto remote repository.  

 Connecting to GitHub using ssh

Open Git Bash.

Paste the text below, substituting in your GitHub email address.

$ ssh-keygen -t ed25519 -C "your_email@example.com"

OR

    ssh-keygen

# start the ssh-agent in the background
$ eval `ssh-agent -s`

Add your SSH private key to the ssh-agent.

$ ssh-add ~/.ssh/id_ed25519

Add the SSH key to your GitHub account.
$ clip < ~/.ssh/id_ed25519.pub
# Copies the contents of the id_ed25519.pub file to your clipboard

How a Java developer push code onto remote repository-
Map local repo with remote repository - git remote add-

git remote add origin git@github.com:krushnaji/demorepo.git


**1. Working with commits on Git**

HEAD -> ALWAYS represent contents in repository
git log
git diff sjslknvsljvn dlsjfclll

red lines --> newly added lines
green lines --> deleted lines
whilte lines --> not changed lines

git diff HEAD HEAD~1     //SAME AS ABOVE git diff

git diff HEAD HEAD~2 


**2. Know information about specific commit on Git -  **
git show---  ---

i dont want to compare two different commits, i just want to see what changes are done in two specific commit

git show     /use to show changes push through commit

git show 4rf4d4gdf4g564g

I want to see who have changed a specific file

git annotate file-name


$ git annotate file2
0e37ec4b        ( krushnaji     2021-02-16 15:59:21 +0530       1)this is file2

root@DESKTOP-HRRUJAL MINGW64 ~/Desktop/git (master)

in git-hub we have blame option to check line by line changes to file done by whom

3. Working with commits on GitHub --- 

we can go commit option


git checkout dyryfsfsd655sd2s2s   // to go to previous commit



4. Commit changes directly on GitHub---

If we create a readme.md file while creating a repository then one auto commit is initialized


readme.md   //md standsfor   MARK DOWN LANGUAGE

#THIS IS MY REPO

#  ---> TAKE line as a header

readme.md file automatically open ups in the repository



6. Git Branches

1. Why do we need branches---

for better devops process we need branches

default branch master branch....we can delete it 

prod branch


2. Branching strategy to protect working code---


 test branch -----> QA  -----> Prod 


3. Working with branches on GitHub--- 


branch is a snapshot of a working code


4. Working with branches on Git---

$ git branch        //shows you how many branches you have
* master    // * means active branch means you are working on master

$ git branch test   //to create a new branch

root@DESKTOP-HRRUJAL MINGW64 ~/Desktop/git (master)
$ git branch
* master
  test


$ git log
$ git log
commit fb85d614993b0ae7fa6abc137498d9199d42afc4 (HEAD -> master, test)   //one more pointer test representing to same commit

Author: krushnaji <rkrushnaji@gmail.com>
Date:   Tue Feb 16 16:43:56 2021 +0530

    third commit

commit 0e37ec4bd4f00fc16151835a3187c3a317797ccf
Author: krushnaji <rkrushnaji@gmail.com>
Date:   Tue Feb 16 15:59:21 2021 +0530

    my second commit

commit 1519369f9378c482686549c521440c069d2c4318
Author: krushnaji <rkrushnaji@gmail.com>
Date:   Tue Feb 16 15:44:39 2021 +0530

    my first commit
       

git checkout    0e37ec4bd4f00fc16   //to change commit head


git switch - // to go back  to previous i.e. latest from checkout

git checkout test  //we can also checkout to another branch


5. Committing changes on branches--- 
we can use different branches to work with different developers and later merge them

git push origin test
git checkout test   //switch to test branch

6. Merging changes onto master branch from dev---

git merge test   //merging test branch with master branch

git push origin master


7. Resolving merge conflicts---

git checkout -b dev         // -b flag used to create and swich to the branch


7. Working with Team

2. Creating a Pull Request (PR)---  

3. Working with Private Repositories--- 


4. Adding Collaborator to a GitHub Repository--- 

frequent user i.e another developer can be added as acollaborator so that we dont have to approve the pull request again and again

settings --> manage access --> invite a collaborator


5. Creating Protected Branch---

setting --> branches --> branch Protection rule

decide how many reveiwers are there befre approving pull request or commiting change to master branch


6. Tagging a commit--- [ FreeCourseWeb.com ] ---

git tag

8. Reverting Changes


1. Revert changes from working directory---   

git restore filename

or

git checkout filename

these two used to restore previous to recent changes in file

even you can remove changes manually but these two commands are really helpful if we have multiple changes in file and we dont know where are the changes.


2. Reverting changes from Staging Area and Local Repository--- 

Revert changes from working directory
   git restore <file_name> 
          or
   git checkout -- <file_name>
Note: even you can remove changes manually. But if we have updated multiple files and don’t know which lines to remove this command really helps
Revert changes from Staging Area
   git restore --staged <file_name>  #to revert changes from Staging area to working directory  
   git restore <file_name> #to revert changes from working directory  
Revert changes from Local Repository
   git reset HEAD~         # to revert changes from local repo to working directory
   git restore <file_name(s)> # to revert changes from working directory  
Revert changes from Remote Repository
We dont have direct way to do this.


3. Using .gitignore file--- 


9. Other Concepts

1. Git rebase--- 

2. Git fetch Vs Git Pull---


10. DevOps Engineer roles on Git

1. Introduction to Git Project---

