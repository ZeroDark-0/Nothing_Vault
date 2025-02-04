---
date: 2025-01-04T15:52
tags:
  - "#git"
---
### <code style="color : aqua">Source -</code> <iframe title="Git Tutorial For Dummies" src="https://www.youtube.com/embed/mJ-qvsxPHpY?feature=oembed" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 16 / 9; width: 100%; height: 100%;"></iframe>

![[RGB Strip.gif]]

Git and Github are two different things. Git is a software which come with you software (mac or Linux) but for Windows you have to download it. 

==Git== is a memory card for code. Like any file like HTML, CSS, JavaScript or any else, it's a location where we store these files.

Commands for Git- 
- For creating new directory `mkdir name_of_directory`
- and to change directory `cd name_of_directory` or go int that directory.
- `touch file_name` is used to create a file in the directory
- For this download - `git init` this will make a empty repository in your device 
- `git add` to save till the late progress or you can save very specific thing by using `git add index.html` or save everything `git add .` 
- For committing we use `git commit -m 'solution update` here 'git commit' is for commit meanwhile the '-m' is message and describe the changes 'solution update'. 
- Removing a file we use `rm file_name`
- Listing Files in the Working Directory `ls` or Listing Files in a Git Repository `git ls-files` 
- `git log` we look the time we saved changes but it also give you a hash code to go back in the time
- To go back we copy the hash code and use `git checkout the_hashcode` but we are in the different branch. use `git branch` to check which branch you are in.
--- 
#### Now what is ==GitHub==?

GitHub is the web-based platform that hosts git repositories.

- To do so first we create a repository on the GitHub, which give us the instruction to use GitHub to link Git with it.
- The `git remote add origin ---` means the to pull the file to the website.
- And the `git push -u origin branch_name` to pull it to the specific branch(like master or any other).
-  `git checkout -b name_of_the_branch` mean to make a new branch
- To add a file you have to use `touch file_name`.

---
Now, the main thing is that we have to sync to GitHub with our PC and that we call a pull.

To pull a GitHub file we use - `git pull origin master`

![[1-Git (202501041552).png]]


![[2-Git (202501041552).png]]
