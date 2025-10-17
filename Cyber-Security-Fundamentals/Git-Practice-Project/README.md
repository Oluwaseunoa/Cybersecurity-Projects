# Git Practice Project Report
Author: Oluwaseun Osunsola
Environment: Hyper Terminal on Windows
GitHub Link: https://github.com/Oluwaseunoa/Cybersecurity-Projects/tree/main/Cyber-Security-Fundamentals

Welcome to my **Git Practice** project! This report documents a hands-on tutorial walking through the complete Git workflow—from initializing a local repository, creating files, pushing to GitHub, branching, editing, creating pull requests, merging changes, and syncing back locally. 

All steps are illustrated with terminal screenshots for clarity. Follow along to master Git fundamentals!

---

## 📋 Table of Contents
1. [Local Repository Setup](#1-local-repository-setup)
2. [GitHub Remote Repository Creation](#2-github-remote-repository-creation)
3. [Linking & Pushing Local Repo to GitHub](#3-linking--pushing-local-repo-to-github)
4. [Cloning Repository](#4-cloning-repository)
5. [Branching & Editing README](#5-branching--editing-readme)
6. [Pull Request & Merge](#6-pull-request--merge)
7. [Verify Merged Changes](#7-verify-merged-changes)
8. [Sync Local Main Branch](#8-sync-local-main-branch)

---

## 1. Local Repository Setup

### Step 1: Create Project Folder
Created the main project folder using Hyper Terminal.

![Created Git-Practice-Project folder on Hyper Terminal](img/1.Created_Git-Practice-Project_folder_on_Hyper_Terminal.png)

### Step 2: Navigate into Project Folder
`cd` into the newly created folder.

![Navigated into Git-Practice-Project folder](img/2.Navigated_into_Git-Practice-Project_folder.png)

### Step 3: Initialize Git Repository
Run `git init` to turn the folder into a Git repository.

![git init Git-Practice-Project folder](img/2b.git_init_Git-Practice-Project_folder.png)

### Step 4: Create & Edit README.md
Created `README.md` file and added a heading.

![created README file and Added heading to it](img/3.created_README_file_and_Added_heading_to_it.png)

### Step 5: Verify README Creation
Used `ls` command to confirm `README.md` exists.

![confirm that README.md was created with ls command](img/4.confirm_that_README.md_was_created_with_ls_command.png)

### Step 6: Check Git Status
Ran `git status` to see untracked files.

![ran git-status to check untracked files](img/5.ran_git-status_to_check_untracked_files.png)

### Step 7: Stage All Changes
Used `git add .` to stage all changes.

![ran git add . to stage all changes](img/6.ran_git_add_.-to_stage_all_changes.png)

### Step 8: Commit Changes
Committed the staged `README.md` with a message.

![commit changes with README.md](img/7.commit_changes_wit_README-md.png)

---

## 2. GitHub Remote Repository Creation

### Step 9: Open GitHub
Navigated to [github.com](https://github.com) in the browser.

![go to github.com via the browser](img/8.go_to_github-com_via_the_browser.png)

### Step 10: Create New Repository
Clicked the **+ icon** → **New Repository**.

![click the plus icon and then new repository](img/9.click_the_plus_icon_and_then_new_repository.png)

### Step 11: Name & Create Repository
Entered repository name: `Git-Practice-Project` and clicked **Create Repository**.

![name repository and click create repository button](img/10.name_repository_and_click_create_repository_button.png)

### Step 12: Repository Created Successfully
Empty repository ready on GitHub!

![repository successfully created](img/11.repository_successfully_created.png)

---

## 3. Linking & Pushing Local Repo to GitHub

### Step 13: Copy Remote HTTPS Link
Copied the HTTPS link from GitHub repo page.

![copy remote link of github repo](img/12.copy_remote_link_of_github_repo.png)

### Step 14: Link Local to Remote
Used `git remote add origin <URL>` with copied link.

![link local repository to github using the copied link](img/13.link_local_repository_to_github_using_the_copied_link.png)

### Step 15: Verify Remote Link
Ran `git remote -v` to confirm connection.

![verified the git link using git remote-v command](img/14.verified_the_git_link_using_git_remote-v_command.png)

### Step 16: Push to GitHub
Pushed local repo: `git push -u origin main`.

![pushed local repo to github](img/15.pushed_local_repo_to_github.png)

---

## 4. Cloning Repository

### Step 17: Create Clone Folder
Created `CloneRepoFolder` in Documents to clone into.

![create CloneRepoFolder in Documents Folder to clone github repo into](img/17.create_CloneRepoFolder_in_Documents_Folder_to_clone_github_repo_into.png)

### Step 17b: Navigate into Clone Folder
`cd CloneRepoFolder`.

![cd into CloneRepoFolder](img/17b.cd_into_CloneRepoFolder.png)

### Step 18: Copy HTTPS Link Again
Clicked **Code** button → **HTTPS** → Copy link.

![on github repo page click the code button then copy https link](img/16.on_github_repo_page_click_the_code_button_then_copy_https_link.png)

### Step 19: Clone Repository
Ran `git clone <URL>` and `cd` into cloned folder.

![cloned Git Repo into a folder called CloneRepoFolder and cd into it](img/18.cloned_Git_Repo_into_a_folder_called_CloneRepoFolderand_cd_into_it.png)

![changed into the new folder Git-Practice-Project (cloned folder)](img/19.changed_into_the_new_folder_%20Git-Practice-Project(cloned%20folder).png)

---

## 5. Branching & Editing README

### Step 20: Create Feature Branch
`git checkout -b feature-edit-readme`.

![git checkout feature-edit-readme](img/20.git_checkout_feature-edit-readme.png)

### Step 21: Edit README.md
Added a new line to `README.md` on the feature branch.

![edited README.md file on the branch](img/21.edited_README-md_file_on_the_branch.png)

### Step 22: Stage, Commit & Push Branch
`git add .` → `git commit -m "..."` → `git push origin feature-edit-readme`.

![pushed feature-edit-readme branch to github](img/22.pushed_feature-edit-readme_branch_to_github.png)

### Step 23: Branch Visible on GitHub
New branch successfully pushed!

![feature-edit-readme pushed branch now on github](img/23.feature-edit-readme_pushed_branch_now_on_github.png)

---

## 6. Pull Request & Merge

### Step 24: Create Pull Request
Clicked **Compare & pull request**.

![click on create pull request](img/24.click_on_create_pull_request.png)

### Step 25: Merge Pull Request
Reviewed changes and clicked **Merge pull request**.

![click on merge pull request](img/25.click_on_merge_pull_request.png)

### Step 26: Confirm Merge
Clicked **Confirm merge**.

![confirm merge](img/26.confirm_merge.png)

### Step 27: Merge Successful!
Pull request merged into `main` branch.

![successfully merge pull request](img/27.successfully_merge_pull_request.png)

---

## 7. Verify Merged Changes

### Step 28: Open README on GitHub
Navigated back to repo files and opened `README.md`.

![go back to the Repo files and open the README file](img/28.go_back_to_the_Repo_files_and_open_the_README_file.png)

### Step 29: New Line Visible
The added line now appears in `main` branch README!

![the new line is now present in the main branch](img/29.the_new_line_is_now_present_in_the_main_branch.png)

---

## 8. Sync Local Main Branch

### Step 30: Checkout Main Locally
Switched to `main` branch—new line missing locally.

![checkout to main locally confirm new line is missing](img/30.checkout_to_main_locally_confirm_new_line_is_missing.png)

### Step 31: Pull Latest Changes
Ran `git pull origin main`—new line now added locally!

![git pull the new change and confirm new line added locally](img/31.git_pull_the_new_change_and_confirm_new_line_added_locally.png)

---

## 🎉 Summary & Key Learnings

| **Skill Demonstrated** | **Commands Used** |
|------------------------|-------------------|
| Initialize repo | `git init` |
| Create & stage files | `touch`, `git add .` |
| Commit changes | `git commit -m "..."` |
| Link to GitHub | `git remote add origin <URL>` |
| Push to remote | `git push -u origin main` |
| Clone repo | `git clone <URL>` |
| Create branch | `git checkout -b <branch>` |
| Push branch | `git push origin <branch>` |
| Pull changes | `git pull origin main` |

**Total Steps:** 31  
**Time to Complete:** ~30 minutes  
**Status:** ✅ **Complete!**

This project proves I can confidently handle the **full Git workflow** end-to-end. Ready for collaborative coding! 🚀

---

*Authored on October 17, 2025 | [View on GitHub](https://github.com/Oluwaseunoa/Cybersecurity-Projects/tree/main/Cyber-Security-Fundamentals)*