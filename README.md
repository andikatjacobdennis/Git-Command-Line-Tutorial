# Git Command-Line Tutorial

Welcome to the Git Command-Line Tutorial, your comprehensive guide to mastering Git—the most popular version control system used by developers worldwide. Whether you're a beginner looking to get started or an experienced developer aiming to refine your skills, this tutorial will help you understand and effectively use Git commands through the terminal.

---

## **1. Setting Up Git**

### **1.1 Install Git**

- **Installation on Windows**:  
   Download Git from [git-scm.com](https://git-scm.com/) and follow the installation steps.

- **Check Git Version**:  
   - After installation, open **Command Prompt**, **PowerShell**, or **Git Bash**.
   - Type the following command to verify the installation and check the Git version:
     ```bash
     git --version
     ```
   - The output should display the installed version of Git, such as `git version 2.47.0.windows.1`.

- **Optional: Install GitHub Desktop**:  
   - GitHub Desktop is a GUI tool that simplifies Git workflows, making it easier to manage repositories visually.  
   - Download GitHub Desktop from [desktop.github.com](https://desktop.github.com/).  
   - Follow the installation steps and log in with your GitHub account.  
   - You can use GitHub Desktop alongside Git command-line tools for a more flexible workflow.

--- 

### **1.2 Configure Git**

When using Git for the first time, you need to configure some basic settings, such as your name, email, default text editor, and line endings. This ensures that Git can properly track your work and maintain consistency across different systems.

#### **Settings:**
- **Name**: The name associated with your commits.
- **Email**: The email address associated with your commits.
- **Default Editor**: The text editor used by Git for commit messages.
- **Line Endings**: Ensures that line breaks are handled correctly across different operating systems.

#### **Settings Levels:**
Git allows you to specify these configurations at three different levels:
- **System**: Applies to all users of the current computer.
- **Global**: Applies to all repositories for the current user.
- **Local**: Applies only to the current repository.

By default, when using the `--global` flag, you apply the settings to the current user across all repositories.

#### **Commands to Apply Settings**:
To configure Git settings at the global level, you use the following commands in the terminal:

1. **Set Global Username and Email**:
   ```bash
   git config --global user.name "John Doe"
   git config --global user.email "johndoe@example.com"
   ```
   - These details will appear in every commit as the author information.

2. **Set a Default Text Editor**:
   ```bash
   git config --global core.editor "code --wait"
   ```
   - This sets Visual Studio Code as the default editor. The `--wait` flag ensures that Git waits for you to close the editor before proceeding with the commit.
   - For other editors, refer to this link: [associating-text-editors-with-git](https://docs.github.com/en/get-started/getting-started-with-git/associating-text-editors-with-git).
   - **Troubleshooting**:
     - If another editor opens instead of VS Code, verify the configuration with `git config --global --get core.editor`
     - Ensure that the `code` command is correctly installed and accessible in your terminal.

3. **View Global Configuration**:
   ```bash
   git config --list
   ```
   - This command lists all current global Git settings.

4. **Edit Global Configuration**:
   ```bash
   git config --global --edit
   ```
   - This command opens the global Git configuration file in the default text editor, allowing you to modify the settings directly.
   
   **Using the Editor**:
   - **Vim**:
     - Navigate using the arrow keys.
     - Press `i` to enter insert mode and make your changes.
     - To save and exit, press `Esc`, then type `:wq` and press **Enter**.
   
   - **Nano**:
     - Navigate using the arrow keys and edit directly.
     - To save the file, press `Ctrl + O`, then press **Enter**.
     - To exit, press `Ctrl + X`.
   
   - **GUI Editors** (e.g., VS Code):
     - The file opens in your default graphical editor, where you can make changes and save the file normally.

#### **End of Line Handling**:
To ensure consistent line endings across different operating systems, configure the `core.autocrlf` setting:

- **Windows**: Windows uses two special characters to mark the end of a line:
  - Carriage Return: `\r`
  - Line Feed: `\n`
  
  To automatically convert line endings when checking files in and out, use the following command:
  ```bash
  git config --global core.autocrlf true
  ```

- **macOS / Linux**: On macOS and Linux, line endings are marked with a single character (Line Feed: `\n`). To handle line endings correctly when working on these operating systems, use:
  ```bash
  git config --global core.autocrlf input
  ```
  
### **1.3 Getting Help**

To get help with a Git command, you can type the command followed by the `--help` flag. For example, `git config --help` will display detailed help information about the `config` command. Use the **space** bar to scroll through the help content and **Esc** to exit.  
Alternatively, using the `-h` flag provides a shorter summary of the help topics.

### **1.4 Command Line Basics**

Here are some basic commands for navigating and managing directories in the command line:

- **`dir`**  
  Lists the contents of the current directory (Windows command).  
  **Example**:  
  ```bash
  dir
  ```

- **`cd <foldername>`**  
  Changes the current directory.  
  **Example**:  
  ```bash
  cd folder_name
  ```

- **`cls`**  
  Clears the terminal screen (Windows command).  
  **Example**:  
  ```bash
  cls
  ```

- **`cd..`**  
  Moves up one directory level.  
  **Example**:  
  ```bash
  cd..
  ```

- **`mkdir <foldername>`**  
  Creates a new directory with the specified name.  
  **Example**:  
  ```bash
  mkdir new_folder
  ```

- **`tab`**  
  Auto-completes the current command or directory name when you press the "Tab" key (works for files and directories). This helps save time and avoid typos.  
  **Example**:  
  If you're typing a folder name and press "Tab," it will auto-complete the name if there's a match. If there are multiple matches, pressing "Tab" twice will list all options.
  
---

## **2. Creating and Managing Repositories**

### **Scenario 1: Create a New Repository**

1. **Initialize a Local Repository**
   ```bash
   mkdir team-project
   cd team-project
   git init
   ```
   - `mkdir team-project`: Creates a new directory named `team-project`.
   - `cd team-project`: Navigates into the new directory.
   - `git init`: Initializes a Git repository in the directory.

2. **Add Files and Make the First Commit**
   ```bash
   echo "# Team Project" > README.md
   git status
   git add README.md
   git commit -m "Initial commit with README"
   ```
   - `echo "# Team Project" > README.md`: Creates a `README.md` file with the text "# Team Project".
   - `git status`: Confirms the file is untracked before adding it.
   - `git add README.md`: Stages the file for the commit.
   - `git commit -m "Initial commit with README"`: Commits the staged file with a message.

3. **Connect to a Remote Repository**
   ```bash
   git remote add origin https://gitlab.com/username/team-project.git
   ```
   - Links the local repository to the remote repository at the specified URL.

4. **Push Changes to Remote**
   ```bash
   git branch -M main
   git push -u origin main
   ```
   - `git branch -M main`: Renames the current branch to `main`.
   - `git push -u origin main`: Pushes the branch to the remote and sets it as the upstream branch.

---

### **Scenario 2: Clone an Existing Repository**

1. **Clone the Repository**
   ```bash
   git clone https://gitlab.com/username/team-project.git
   cd team-project
   ```
   - `git clone <URL>`: Copies the remote repository to the local system.
   - `cd team-project`: Navigates into the cloned repository.

---

### **Scenario 3: Undo an Accidental `git init`**

If you mistakenly ran `git init` in the wrong directory on a Windows system, follow these steps to remove it:

1. **Navigate to the Directory**  
   Open Command Prompt or PowerShell and navigate to the directory where you accidentally initialized Git:  
   ```cmd
   cd C:\path\to\wrong-directory
   ```

2. **Delete the `.git` Folder**  
   The `.git` folder is hidden by default. Use one of the following commands to remove it:

   - **Command Prompt**:  
     ```cmd
     rmdir /s /q .git
     ```
     - `/s`: Removes all files and subdirectories in the `.git` folder.  
     - `/q`: Quiet mode, suppresses confirmation prompts.

   - **PowerShell**:  
     ```powershell
     Remove-Item -Recurse -Force .git
     ```
     - `-Recurse`: Ensures all contents in `.git` are removed.  
     - `-Force`: Bypasses confirmation prompts.

3. **Verify the Folder is Removed**  
   List the contents of the directory to ensure the `.git` folder is no longer present:  
   ```cmd
   dir /a
   ```
   If `.git` does not appear, the repository has been removed.

---

### **Scenario 4: Unstage Changes**

If you accidentally added files to the staging area using `git add`, you can unstage them without removing your local changes:

1. **Check the Status of Staged Changes**
   ```bash
   git status
   ```
   - Lists the files in the staging area (in green) and any untracked or modified files (in red).

2. **Unstage a Single File**
   ```bash
   git reset <file-name>
   ```
   - Removes the file from the staging area while keeping the changes in your working directory.

   **Example:**
   ```bash
   git reset README.md
   ```

3. **Unstage All Files**
   ```bash
   git reset
   ```
   - Removes all files from the staging area, keeping the changes in your working directory.

4. **Verify Changes are Unstaged**
   ```bash
   git status
   ```
   - Confirms the files are no longer in the staging area but still show as modified or untracked.

### **Scenario 5: Managing Staged and Unstaged Changes**

#### **1. Stage Specific Files**

Suppose you modified two files: `index.html` and `style.css`. To stage only `index.html`, use:
```bash
git add index.html
```
- **Explanation**: This stages only the `index.html` file while leaving `style.css` unstaged.

---

#### **2. Stage All Modified Files**

To stage **all modified files** in the current directory and its subdirectories, use:
```bash
git add .
```
- **Explanation**: This stages all changes (including modified and newly created files) in the directory, but **does not stage deleted files**.

---

#### **3. Unstage a Specific File**

If you accidentally staged `style.css` and want to unstage it, use:
```bash
git reset style.css
```
- **Explanation**: This removes `style.css` from the staging area but keeps your local changes in the working directory.

---

#### **4. Commit Staged Changes**

After staging `index.html`, you can commit the changes with a message:
```bash
git commit -m "Update index.html layout"
```
- **Explanation**: This commits only the staged file (`index.html`).

---

#### **5. Discard Unstaged Changes**

If you’ve made unwanted changes to `style.css` and want to revert it to the last committed version, use:
```bash
git checkout -- style.css
```
- **Explanation**: This restores `style.css` to its last committed state, discarding any local modifications.

---

#### **6. Stage Changes Using `git add -u` and `git add -A`**

- **`git add -u`**: Stages **only tracked files** (modified and deleted), but **does not include new files**.

   **Example:**
   ```bash
   git add -u
   ```
   - If you have modified `index.html`, deleted `style.css`, and created a new file `newfile.js`, this will:
     - Stage the changes to `index.html` (modified)
     - Stage the deletion of `style.css`
     - **NOT** stage `newfile.js` because it's an untracked file.

- **`git add -A`**: Stages **all changes**, including modifications, deletions, and **new files**.

   **Example:**
   ```bash
   git add -A
   ```
   - This will:
     - Stage the changes to `index.html`
     - Stage the deletion of `style.css`
     - **Stage `newfile.js`**, even though it's new and untracked.

---

#### **7. Verify Staging**

After staging, use `git status` to verify what has been staged and what remains untracked or modified:
```bash
git status
```
- **Explanation**: This will show you which files are staged for commit, which are modified but unstaged, and which are untracked.

---

### **Practical Example**

Let’s simulate the following steps:
1. Modify `app.js` and `config.json`.
2. Stage and unstage changes:
   ```bash
   git add app.js
   git reset app.js
   ```
3. Commit only `config.json`:
   ```bash
   git add config.json
   git commit -m "Update configuration settings"
   ```
4. Discard changes in `app.js`:
   ```bash
   git checkout -- app.js
   ```

---

### **Summary of `git add -u` vs `git add -A`:**

| Command            | Stages                                      |
|--------------------|---------------------------------------------|
| `git add -u`        | Stages modified and deleted **tracked** files only. |
| `git add -A`        | Stages **all** changes: modified, new (untracked), and deleted files. |

---

## **3. Branch Management**

### **Scenario 1: Create and Use Branches**

1. **Create a New Branch**
   ```bash
   git checkout -b feature/add-login
   ```
   - `git checkout -b <branch-name>`: Creates and switches to the new branch `feature/add-login`.

2. **Push the New Branch**
   ```bash
   git push origin feature/add-login
   ```
   - `git push origin <branch-name>`: Pushes the new branch to the remote repository.

3. **Merge Branch into Main**
   ```bash
   git checkout main
   git pull origin main
   git merge feature/add-login
   git push origin main
   ```
   - `git checkout main`: Switches to the `main` branch.
   - `git pull origin main`: Updates the local `main` branch with the latest changes from the remote.
   - `git merge feature/add-login`: Merges `feature/add-login` into `main`.
   - `git push origin main`: Pushes the merged changes to the remote.

4. **Delete a Branch**
   ```bash
   git branch -d feature/add-login         # Delete locally
   git push origin --delete feature/add-login  # Delete remotely
   ```
   - `git branch -d <branch-name>`: Deletes the branch locally.
   - `git push origin --delete <branch-name>`: Deletes the branch from the remote repository.

---

### **Scenario 2: Rename a Feature Branch**

1. **Rename the Current Branch**
   If you are on the branch you want to rename, use:
   ```bash
   git branch -m <new-branch-name>
   ```
   - `git branch -m <new-branch-name>`: Renames the current branch to `<new-branch-name>`.

2. **Push the Renamed Branch to Remote**
   ```bash
   git push origin -u <new-branch-name>
   ```
   - `git push origin -u <new-branch-name>`: Pushes the renamed branch to the remote and sets it to track the remote branch.

3. **Delete the Old Branch from Remote** (optional)
   ```bash
   git push origin --delete <old-branch-name>
   ```
   - `git push origin --delete <old-branch-name>`: Deletes the old branch from the remote repository.

4. **Rename a Branch Not Currently Checked Out**
   If you're not currently on the branch you want to rename, use:
   ```bash
   git branch -m <old-branch-name> <new-branch-name>
   ```
   - `git branch -m <old-branch-name> <new-branch-name>`: Renames the branch from `<old-branch-name>` to `<new-branch-name>`.

5. **Update Your Local References**
   If necessary, update your local tracking references:
   ```bash
   git fetch --all
   ```
   - `git fetch --all`: Fetches the latest information from the remote repository.

---

### **Scenario 3: Rebase Branches**

1. **Rebase Feature Branch onto Main**
   ```bash
   git checkout feature/add-login
   git pull origin main --rebase
   ```
   - `git pull origin main --rebase`: Updates the `feature/add-login` branch by rebasing it onto `main`.

2. **Resolve Conflicts During Rebase**
   ```bash
   git add <file-name>
   git rebase --continue
   ```
   - `git add <file-name>`: Marks the file as resolved.
   - `git rebase --continue`: Continues the rebase process.

3. **Push Rebasing Changes**
   ```bash
   git push origin feature/add-login --force
   ```
   - `git push origin <branch-name> --force`: Overwrites the remote branch with the rebased history.

---

### **Scenario 4: Reset Local Branch to Match Remote**

When the local branch and remote branch have diverged, and you want to align your branch with the `master` branch by discarding local changes:

1. **Fetch the Latest Changes**
   ```bash
   git fetch origin
   ```
   - `git fetch origin`: Retrieves the latest updates from the remote repository, including changes to the `master` branch.

2. **Checkout the Feature Branch**
   ```bash
   git checkout feature-branch-name
   ```
   - `git checkout feature-branch-name`: Switches to the feature branch you want to reset.

3. **Reset the Branch to Match `master`**
   ```bash
   git reset --hard origin/master
   ```
   - `git reset --hard origin/master`: Resets the feature branch to exactly match the `master` branch, discarding all local changes and commits.

4. **Push the Reset Branch**
   ```bash
   git push --force
   ```
   - `git push --force`: Updates the remote branch with the reset changes, overwriting the remote branch history.

## **4. Viewing and Modifying History**

### **Scenario 1: View Commit History**
```bash
git log --oneline --graph --decorate --all
```
- `--oneline`: Displays a simplified one-line format for each commit.
- `--graph`: Shows a visual representation of the branch history.
- `--decorate`: Adds branch and tag names to the log.
- `--all`: Displays all branches and their history.

---

### **Scenario 2: Interactive Rebase**
1. **Rebase the Last 3 Commits**
   ```bash
   git rebase -i HEAD~3
   ```
   - `git rebase -i HEAD~3`: Starts an interactive rebase for the last 3 commits.

2. **Edit Commit List**
   - In the editor, mark commits as:
     - `pick`: Keep the commit.
     - `squash`: Combine the commit with the previous one.
     - `drop`: Remove the commit.

3. **Push Changes After Rebase**
   ```bash
   git push origin feature/add-login --force
   ```

---

### **Scenario 3: Cherry-Pick Commits**
1. **Apply a Specific Commit**
   ```bash
   git cherry-pick <commit-hash>
   ```
   - `git cherry-pick <commit-hash>`: Applies the specified commit to the current branch.

---

## **5. Undoing Changes**

### **Scenario 1: Undo the Last Commit**
1. **Undo the Commit but Keep Changes**
   ```bash
   git reset --soft HEAD~1
   ```
   - `--soft`: Removes the commit but keeps changes staged.

2. **Undo the Commit and Discard Changes**
   ```bash
   git reset --hard HEAD~1
   ```
   - `--hard`: Removes the commit and discards all changes.

---

### **Scenario 2: Revert a Commit**
1. **Revert a Specific Commit**
   ```bash
   git revert <commit-hash>
   ```
   - `git revert <commit-hash>`: Creates a new commit that reverses the specified commit.

---

## **6. Managing Conflicts**

### **Scenario: Resolve Merge Conflicts**
1. **Merge a Branch**
   ```bash
   git merge feature/add-login
   ```
   - Attempts to merge `feature/add-login` into the current branch.

2. **Resolve Conflicts**
   - Edit the conflicting file(s) and remove conflict markers:
     ```text
     <<<<<<< HEAD
     Line from main
     =======
     Line from feature/add-login
     >>>>>>> feature/add-login
     ```
   - Save the changes and mark as resolved:
     ```bash
     git add <file-name>
     git merge --continue
     ```
---

## **7. Stashing Work**

### **Scenario 1: Save Changes Temporarily**
1. **Stash Changes**
   ```bash
   git stash
   ```
   - Saves uncommitted changes and cleans the working directory.

2. **Apply a Stash**
   ```bash
   git stash apply stash@{0}
   ```
   - Applies the specified stash without removing it from the stash list.

3. **Drop a Stash**
   ```bash
   git stash drop stash@{0}
   ```
   - Deletes the specified stash from the stash list.

---

### **Scenario 2: Save Changes with a Message**
1. **Stash Changes with a Description**
   ```bash
   git stash push -m "Description of stash"
   ```
   - Saves changes with a descriptive message for easier identification.

---

### **Scenario 3: Stash Only Specific Files**
1. **Stash Specific Files**
   ```bash
   git stash push -m "Description" path/to/file
   ```
   - Stashes only the specified files.

---

### **Scenario 4: Stash Untracked Files**
1. **Include Untracked Files**
   ```bash
   git stash push -u
   ```
   - Stashes both tracked and untracked files.

2. **Include All Files**
   ```bash
   git stash push -a
   ```
   - Stashes all files, including ignored ones.

---

### **Scenario 5: View and Manage Stashes**
1. **List Stashes**
   ```bash
   git stash list
   ```
   - Displays all stashes with their index and description.

2. **Show Stash Details**
   ```bash
   git stash show stash@{0}
   ```
   - Displays changes saved in the specified stash.

3. **View Detailed Stash Changes**
   ```bash
   git stash show -p stash@{0}
   ```
   - Shows detailed differences stored in the stash.

---

### **Scenario 6: Apply and Clear Stash Simultaneously**
1. **Pop a Stash**
   ```bash
   git stash pop stash@{0}
   ```
   - Applies the specified stash and removes it from the stash list.

---

### **Scenario 7: Stash for a Specific Branch**
1. **Create a Stash for a Branch**
   ```bash
   git stash push -m "stash for branch-name"
   ```
   - Helps to identify the stash as related to a specific branch.

2. **Apply a Stash from Another Branch**
   ```bash
   git stash apply stash@{n}
   ```
   - Applies a stash created in another branch.

---

### **Scenario 8: Clear All Stashes**
1. **Clear Entire Stash List**
   ```bash
   git stash clear
   ```
   - Deletes all stashes.

2. **Remove Stashes up to a Specific Index**
   ```bash
   git stash drop stash@{n}
   ```
   - Removes stashes individually.

Here’s a simplified and beginner-friendly version with clear explanations and mock examples for each scenario. 

---

## **8. Deleting Repositories**

### **Scenario 1: Remove Both Local and Remote Repository**

1. **Delete the Local Repository**
   ```bash
   cd ..
   rm -rf my-project
   ```
   **Example:**
   - You’re working on a project called `my-project`. To remove it from your computer, go to its parent directory (`cd ..`) and delete the folder using `rm -rf my-project`.

2. **Delete the Remote Repository Using GitHub API**
   ```bash
   curl -X DELETE -H "Authorization: token ghp_12345" \
   "https://api.github.com/repos/john-doe/my-project"
   ```
   **Example:**
   - Replace `ghp_12345` with your personal GitHub token and `john-doe/my-project` with your GitHub username and repository name. 
   - This command removes the repository from your GitHub account.

---

### **Scenario 2: Delete Only the Local Repository**

1. **Remove the Local Folder**
   ```bash
   cd ..
   rm -rf my-project
   ```
   **Example:**
   - If you want to keep the remote repository but delete the local files, follow the same steps as above to remove the local folder.

---

### **Scenario 3: Unlink Local Repository from Remote**

1. **Remove the Remote Connection**
   ```bash
   git remote remove origin
   ```
   **Example:**
   - Let’s say you cloned a repository but no longer need it linked to GitHub. Run this command in the project folder.  
   - After this, `git push` or `git pull` won’t work because the link to GitHub is gone.

---

### **Scenario 4: Delete a Remote Repository Using GitHub Website**

1. **Access GitHub Settings**
   - Go to your repository on GitHub: `https://github.com/john-doe/my-project`.
   - Click on **Settings** > Scroll to **Danger Zone**.

2. **Delete the Repository**
   - Click **Delete this repository**.
   - Type the repository name (`john-doe/my-project`) to confirm.

   **Example:**
   - If `my-project` is no longer needed, this is the easiest way to delete it from GitHub without using commands.

---

### **Scenario 5: Delete a Remote Repository via SSH**

1. **Remove Repository Using SSH**
   ```bash
   ssh git@github.com rm -rf /repos/john-doe/my-project.git
   ```
   **Example:**
   - If you have SSH access to GitHub (e.g., your company uses SSH keys), this command deletes the repository directly. Replace `john-doe/my-project.git` with your repository path.

---

### **Scenario 6: Archive a Repository Instead of Deleting**

1. **Archive on GitHub**
   - Navigate to `https://github.com/john-doe/my-project`.
   - Go to **Settings** > **Danger Zone** > Click **Archive this repository**.

   **Example:**
   - If you don’t want to delete your project but want to make it read-only for everyone, archiving is a safer option.

---

### **Scenario 7: Remove All Repository History Locally**

1. **Delete Git History and Reinitialize**
   ```bash
   rm -rf .git
   git init
   ```
   **Example:**
   - If `my-project` has too much clutter in its Git history, this clears everything.  
   - Be careful: This starts a fresh Git repository with no previous history.

---

### **Scenario 8: Delete a Bare Repository**

1. **Remove a Bare Repository**
   ```bash
   rm -rf my-project.git
   ```
   **Example:**
   - A bare repository is used for server storage (e.g., central Git repositories). If you no longer need it, simply delete the folder as shown.

---

### Mock Example Walkthrough

Let’s say your repository is **`john-doe/my-project`**, and you:
- No longer need it locally → Use **Scenario 2**.
- Want to delete it from GitHub → Use **Scenario 1** or **Scenario 4**.
- Want to keep it but unlink it from GitHub → Use **Scenario 3**.

Here are additional topics and scenarios that can be covered to make your Git tutorial more comprehensive and versatile:  

---

### **9. Collaboration with Others**  
Git shines in teamwork! Learn how to collaborate effectively.  

1. **Forking and Pull Requests**  
   - How to fork a repository for contributing.  
   - Create and submit a pull request to propose changes.  

2. **Working with Remote Repositories**  
   - Add a new remote repository:  
     ```bash
     git remote add upstream <URL>
     ```  
   - Fetch changes from another remote:  
     ```bash
     git fetch upstream
     ```  

3. **Tracking Changes from Multiple Contributors**  
   - Use `git blame` to identify who modified specific lines.  
   - Resolve conflicts in collaborative projects.  

4. **Setting Up Permissions and Collaborators**  
   - Manage repository permissions using GitHub or GitLab.  

---

### **10. Automation and Advanced Tools**  
Streamline your workflow by integrating Git with other tools or automating tasks.  

1. **Git Hooks**  
   - Set up pre-commit and post-commit hooks to enforce coding standards:  
     ```bash
     echo "lint your code here!" > .git/hooks/pre-commit
     chmod +x .git/hooks/pre-commit
     ```  

2. **Using Git Aliases**  
   - Save time with custom shortcuts:  
     ```bash
     git config --global alias.st status
     ```  

3. **Git with CI/CD**  
   - Push changes to trigger CI/CD pipelines for automated testing or deployment.  

---

### **11. Managing Large Repositories**  

1. **Git LFS (Large File Storage)**  
   - Track large files:  
     ```bash
     git lfs track "*.psd"
     ```  

2. **Sparse Checkout**  
   - Download only specific parts of a repository:  
     ```bash
     git sparse-checkout set folder-name
     ```  

3. **Prune Unused Objects**  
   - Clean up unused objects to save space:  
     ```bash
     git gc --prune=now
     ```  

---

### **12. Git for Debugging**  

1. **Bisecting to Find Bugs**  
   - Use `git bisect` to locate problematic commits:  
     ```bash
     git bisect start
     git bisect bad
     git bisect good <commit>
     ```  

2. **Debugging Merge Conflicts**  
   - Use `git rerere` (reuse recorded resolution):  
     ```bash
     git config --global rerere.enabled true
     ```  

---

### **13. Security Best Practices**  

1. **Remove Sensitive Data from History**  
   - Use `git filter-repo` or `BFG Repo Cleaner` to remove sensitive data.  

2. **Signing Commits**  
   - Sign commits with GPG for added authenticity:  
     ```bash
     git config --global user.signingkey <your-key>
     git commit -S -m "Signed commit"
     ```  

3. **Check for Vulnerabilities**  
   - Use tools like GitHub’s Dependabot to scan for vulnerabilities in dependencies.  

---

### **14. Customization and Optimization**  

1. **Customize Git Logs**  
   - Pretty-print logs for better readability:  
     ```bash
     git log --pretty=format:"%h - %an, %ar : %s"
     ```  

2. **Optimizing Repository Performance**  
   - Compact the repository for faster performance:  
     ```bash
     git repack -Ad
     git gc --aggressive
     ```  

---

### **15. Exploring Git Ecosystem**  

1. **Integrating with GUI Clients**  
   - Explore tools like SourceTree, GitKraken, or GitHub Desktop.  

2. **Exploring Advanced Hosting Platforms**  
   - Compare GitHub, GitLab, and Bitbucket for hosting repositories.  

3. **Exploring Git Workflows**  
   - Learn about GitFlow, GitHub Flow, and Trunk-based development to find the best workflow for your team.  

---

### **16. Git Tips and Tricks**  

1. **Using `git restore` for Undoing Changes**  
   ```bash
   git restore <file>
   ```  

2. **Edit Last Commit Without Changing Hash**  
   ```bash
   git commit --amend --no-edit
   ```  

3. **Quick Switch Between Branches**  
   - Return to the previous branch with:  
     ```bash
     git switch -
     ```  

4. **Save and Load Patches**  
   - Save changes as a patch:  
     ```bash
     git diff > changes.patch
     ```  
   - Apply a patch later:  
     ```bash
     git apply changes.patch
     ```  
