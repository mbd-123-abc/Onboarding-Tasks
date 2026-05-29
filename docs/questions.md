Q1. What GitHub features allow contributors to make simple code changes directly from the web browser? Describe at least two. 

Edit (github.com) and Terminal (github.dev)

Q2. What are the lifecycle phases of a GitHub Codespace, and what happens in each phase? 

Creation > Active > Stopped > Rebuild > Deletion 

Q3. What happens to your work if you stop a GitHub Codespace without committing your changes? 

Remote may or may not contain changes based on wether you saved. You may lose work. Things get auto-deleted in 30 days of inactivity.

Q4. Who should enable two-factor authentication (2FA) on GitHub, and why? 

Everyone to keep their code and secrets safe 

Q5. What permission levels exist for repositories owned by a personal GitHub account? 

1 Owner and Collaborators 

Q6. What repository visibility options does GitHub provide, and when would you use each? 

Public/Private 
Public for non-sensative code you don't mind others seeing and using 
Private by default 

Q7. What is the purpose of a CODEOWNERS file? 

It tells everyone about roles and allows for accountability. 

Q8. How can you enforce that status checks must pass before merging into the main branch? 

Setting > Branches > Rules > Require Status Checks 

Q9. What steps can you take to ensure changes to main require approval from at least two reviewers? 

Setting > Branches > Rules > Enable dismiss stale reviews, prevent self-review + Require 2 Reviews 

Q10. What is CodeQL, and how is it used in GitHub? 

It's the feature that allows you to search your code for specific functions and keywords like a database.

Q11. What is a fork in GitHub, and when should you use one?

A personal copy of someone elses repo. You should use them when you don't have access and would like to propose a change anyway. 

Q12. What is a pull request in GitHub? 

When you're asking others to double check your finished work to check if it can be pulled into main. 

Q13. When creating a pull request from feature-a into main, which branch is the base and which is the compare? 

main is the base and feature is the compare

Q14. What are draft pull requests, and when should they be used? 

Essentially unfinished pull requests so your coworkers know what you're working on and don't overwrite/work on the same feature. 
