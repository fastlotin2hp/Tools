# 1. git configuration
  git --version
  git config --help
  git config --global user.name "first_name last_name"
  git config --global user.email.com "abc@de.com"
  
  // show the all configs
  git config --list
  
# 2. git init
to create .git directory
  
to remove the git , under that directory 
  ```bash 
  rm -rf .git
  ```
.gitignore file    
  ```bash
  touch .gitignore
  ```

# 3. git add
    
//add all to stage.
  ```bash 
  git add -A
  ```
# 3. git reset

  unstage sepcific file
  ```bash 
  git reset file_name
  ```
  unstage all file
  
  ```bash 
  git reset
  ```
  
# 4. git commit

  unstage sepcific file
  
  ```bash 
  git commit -m "comments"
  ```

# 5. git clone

  ```bash 
  git clone <url> <dir>
  ```
  clone locally
  
  ```bash 
  git clone ../remote_repo.git .
  ```
  
 # 5. git pull/push

  pull
  ```bash 
  git pull original master
  ```
  push
  ```bash 
  git push original master
  ```

# 8. loging
  - git log shorten_title --oneline -3
  - git log --graph --oneline --decorate --all  
# 9 commite
    git show HEAD
  

# 10 Branch
    cat .git/HEAD 
    cat -la .git/refs/heads
    cat -la .git/refs/heads/master ==> return a sha of the HEAD
  
    git branch 
            --branch_name >>to create a new branch
              
    git checkout [branch or file]
               new_branch 
               -b new_branch >> create and switch to new branch at the same time
               
   --compare branches
      git diff master..new_branch 
      git diff --color-words master..new_branch
      git diff --color-words master..new_branch^
      git diff --color-words master..new_branch~3
  
  --if one branch totally contain others
    git branch --merged
    
  --rename branch
     git branch -m     new_branch descriptive_branch_name
     git branch --move new_branch descriptive_branch_name
    
  --delete branch
    git branch -d       new_branch
               --delete new_branch
               
  delete the remote branch  
  ```bash 
  git push origin --delete branch_name               
  ``` 
            
# 11 Merging 
    git merge new_branch
    git merge --no-ff branch [force to not use fast-forward merge]
    git merge --ff-only branch [only use fast-forward if possible,othrewise abort]
    git merge --abort
  
    git mregetool [for the third party merging tool]
  
# 12 stash 
    git stash save "save temp change"
    git stash list
    git stash show stash@{0}
    git stash show -p stash@{0}
  -- to grep the stashed file
    git stash apply stash@{0}
    git stash pop   stash@{0} [replace ,and remove it from stash]
  --delet stashed file
      git stash drop stash@{0}
      git stash clear [remove all stashes]

# appendix show the current branch
  ```bash
  export ps1='\W$(__git_ps1 "(%s)" > )'
  export ps1='$(__git_ps1 "(%s)" > )'
  ```
# a-1 Basic writing and formatting syntax
  https://help.github.com/articles/basic-writing-and-formatting-syntax/
