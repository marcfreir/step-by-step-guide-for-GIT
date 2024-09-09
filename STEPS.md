# Git & GitHub Step-by-Step Guide

This is a basic pipeline to use git and GitHub (probably all you need, most of the time).

by [Marc Freir](https://github.com/marcfreir), 2024

### Prerequisites
- **Install Git**: Ensure that Git is installed on your local machine. You can download it [here](https://git-scm.com/downloads).
- **Check Git installation**: Run `git --version` to verify Git is installed.
- **SSH Key Setup**: Make sure you have an SSH key (`id_rsa.pub`) for authentication. If you don’t have one, generate it using the steps in this [tutorial video](https://www.youtube.com/watch?v=RGOj5yH7evk). Add the public key to your GitHub or Bitbucket account.

---

### Initial Repository Setup (Cloning or Connecting to an Existing Repo)

#### 1. **Initialize Git in Your Local Repository**
If you are working with an existing project but haven’t yet connected it to Git:
```bash
git init
```

#### 2. **Link Your Local Repository to a Remote**
```bash
git remote add origin git@github.com:yourusername/your-repository.git
```

#### 3. **Set Your Git Identity (First Time Setup)**
If this is your first time using Git, configure your username and email globally:
```bash
git config --global user.name "yourusername"
git config --global user.email "your.email@example.com"
```

---

### Working with the Repository

#### 4. **Pulling the Latest Changes**
Before making any changes, ensure you have the latest version of the repository:
```bash
git pull origin main  # or 'master' if your repo uses it
```
*Note: GitHub has transitioned from `master` to `main` as the default branch name. If unsure, verify by checking your repository.*

---

#### 5. **Adding Files for Commit**
To stage files for commit:
- Add all files:
    ```bash
    git add -A
    ```
- Add specific files:
    ```bash
    git add filename
    ```

#### 6. **Committing Changes**
To commit your changes with a descriptive message:
```bash
git commit -m "Brief, imperative description of changes"
```
For exemple:
```bash
git commit -m "Add delete button to main window"
```

#### 7. **Pushing Changes to the Remote Repository**
Push your changes to the remote repository:
```bash
git push origin main  # or 'master' for old repositories
```

If the default branch is `main`, use:
```bash
git push origin HEAD:main
```

---

### Handling Branches

#### 8. **Check Out and Switch Between Branches**
To switch between branches or create a new branch:
```bash
git checkout <branch_name>
```

#### 9. **Creating a New Branch and Setting Upstream**
```bash
git checkout -b <new_branch_name>  # Create a new branch
git push -u origin <new_branch_name>  # Push to remote and track the branch
```

#### 10. **Syncing with Remote Branch**
To set the tracking branch (when Git prompts that there is no tracking info):
```bash
git branch --set-upstream-to=origin/main  # or 'master'
```

---

### Dealing with Common Errors

#### 11. **Resolve "Pull is Not Possible Due to Unmerged Files"**
If you get an error about unmerged files:
```bash
git status  # Check which files have conflicts
git add <file>  # Mark the conflicted files as resolved
git commit -m "Resolve merge conflicts"
git pull
```

---

### Managing the Default Branch

If your default branch is still `master` and you want to rename it to `main`, follow these steps:

#### 12. **Rename the `master` Branch to `main`**
1. Rename the branch locally:
    ```bash
    git branch -m master main
    ```

2. Push the new `main` branch to the remote repository:
    ```bash
    git push -u origin main
    ```

3. Update the symbolic reference of the `HEAD`:
    ```bash
    git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
    ```

4. Change the default branch in your GitHub settings:
   Follow [this guide](https://docs.github.com/en/github/administering-a-repository/setting-the-default-branch).

5. Delete the `master` branch from the remote:
    ```bash
    git push origin --delete master
    ```

---

### Undoing Changes

#### 13. **Reset Staged Files**
If you mistakenly staged files, you can reset them:
```bash
git reset <file>  # Unstage a specific file
git reset  # Unstage all files
```

#### 14. **Amend the Last Commit**
To change the last commit message or add changes:
```bash
git commit --amend -m "Updated message"
git push --force-with-lease  # Push amended commit
```

---

### Starting a New Repository from an Existing Remote Repo

#### 15. **Clone an Existing Repository**
To clone a repository and create a local copy:
```bash
git clone git@github.com:yourusername/your-repository.git
```

#### 16. **Initialize and Pull from an Existing Remote**
If the repository exists online, but your local repository is empty:
1. Initialize Git locally:
    ```bash
    git init
    ```

2. Add the remote repository:
    ```bash
    git remote add origin git@github.com:yourusername/your-repository.git
    ```

3. Pull the remote repository:
    ```bash
    git pull origin main  # or 'master'
    ```

---

### Best Practices

- **Use Branches**: Create a branch for new features or fixes.
- **Descriptive Commit Messages**: Use concise messages in the imperative mood, like "Fix bug in login module."
- **Pull Regularly**: Always pull changes from the remote before starting new work to avoid merge conflicts.
- **Resolve Conflicts**: Use `git status` frequently to monitor potential issues.

---

This updated documentation provides a more structured, clear, and concise guide for using Git and GitHub effectively. Each section is categorized by task, allowing users to quickly reference what they need.