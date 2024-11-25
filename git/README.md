
```English
An imperative statement is a sentence that gives a command, request, or instruction: 
They are verb-beginning  sentences 
"Complete the experiment by Friday", "Wash the dinner plates", "Measure two cups of flour" 

While the imperative statements might read: 

Install an operating system on this machine
Install these dependencies
Download code from this URL
Move the code to this directory
Do this 3 times for 3 other machines

The declarative version of this would simply read: 4 machines have software from this URL, installed at this directory.

IaC encourages and promotes declarative system administration tools over custom imperative solutions. This led to the emergence of technologies like Docker Containers, Ansible, Terraform, and Kubernetes, which utilize static declarative configuration file

```
- Declarative software follows a declaration of an expected state

# Git Beginner's Lecture
================================================
# Definition
# Folder Structure( ```ls .git/**/*```)
# Architecture (Single component or multi-component)
# Workflow
# Operation
=====================================================



### 1. **What is Git?**

Git is a tool used to manage changes in code or documents over time. It allows you to track versions, collaborate with others, and manage the history of a project.

### 2. **What Git is:**
- **Git** is a **distributed version control system** (VCS). It is a tool that helps you manage and track changes to files, typically source code in software development projects.
- It operates by keeping a **local copy** (repository) of your project on your computer, and it also allows you to interact with **remote repositories** (like on GitHub, GitLab, Bitbucket, etc.).
  

### 2. **Folder structure:**
- check [git folder structure](../git_folder_structure.md)
  



### **Architecture of git**
No, **Git** is not a "client" in the typical sense, but it does operate in a way that can involve client-server interaction when you're working with remote repositories.


Git's architecture is based on a **distributed version control system** (DVCS), which means that every user has a full copy of the repository (including its history) on their own machine. This is different from a centralized version control system (CVCS) like SVN or CVS, where there is a single central repository.

### High-Level Git Architecture Overview:

1. **Working Directory (Working Tree)**:
   - This is the folder or directory where you actually work on the project. It contains all the files you're editing or adding.
   - It's what you see and interact with on your local machine. Any file you create or modify is in your working directory.

2. **Staging Area (Index)**:
   - The staging area, also called the **index**, is like a buffer between the working directory and the repository. It's where you prepare changes before committing them.
   - When you use the `git add` command, you move files from your working directory to the staging area. This means you're telling Git, "These are the changes I want to commit."
   - It's a temporary area to accumulate changes before they are permanently stored in the repository.

3. **Repository (Local Repository)**:
   - This is where Git stores all the history of your project, including commits, branches, and tags. It is stored in a hidden folder called `.git` in your project directory.
   - Inside the repository, there are several components:
     - **Commits**: Snapshots of your project at specific points in time.
     - **Branches**: Branches represent different lines of development in your project.
     - **Tags**: Tags are like "labels" for specific commits (e.g., marking a release).

4. **Local Git Database (Git Objects)**:
   - **Git objects** are the fundamental building blocks of the Git system and are stored in your local `.git` directory.
   - There are several types of Git objects:
     - **Blob**: Stores the contents of files.
     - **Tree**: Stores directories and file names, linking blobs and trees to represent the structure of a directory.
     - **Commit**: Records the changes made to files, the tree structure, and the author’s metadata (name, date).
     - **Tag**: A reference to a specific commit, often used for marking release points (like v1.0).

5. **Remote Repositories**:
   - A **remote repository** is a copy of your repository stored on a server (like GitHub, GitLab, or Bitbucket).
   - While your local repository is the version of the project you're working with, remote repositories act as centralized servers where collaborators can push and pull changes.
   - Git is **distributed**, so each developer has their own local repository and can work offline. Changes are only synchronized (pushed or pulled) when necessary.

### Git Workflow:

1. **Working Directory → Staging Area**:
   - You make changes to files in your working directory (e.g., editing a file, creating a new one).
   - Once you've made changes, you **stage** them (using `git add`) to indicate which changes you want to include in your next commit.

2. **Staging Area → Local Repository**:
   - Once you've staged the changes, you can commit them (using `git commit`). This creates a snapshot of your changes and saves it into the **local repository**.
   - The commit is stored in the Git database as a commit object, and Git adds metadata like author, timestamp, and commit message.

3. **Local Repository → Remote Repository**:
   - After committing your changes locally, you can synchronize them with a remote repository by using `git push`.
   - When you collaborate with others, you use `git pull` to fetch and merge changes from the remote repository into your local repository.

---

### Git Architecture Diagram (Conceptual Overview)

```
+-------------------+        +-----------------------+
|                   |        |                       |
| Working Directory | <----> | Staging Area (Index)  |
|                   |        |                       |
+-------------------+        +-----------------------+
               |
               v
+----------------------------------------+
|                                        |
|        Local Git Repository (.git)     |
| - Commits                              |
| - Branches                             |
| - Tags                                 |
| - Git Objects (Blobs, Trees, Commits)  |
|                                        |
+----------------------------------------+
               |
               v
+----------------------------------------+
|                                        |
|          Remote Git Repository         |
| (GitHub, GitLab, Bitbucket, etc.)      |
|                                        |
+----------------------------------------+
```

### Git's Core Components:

1. **Working Directory**:  
   - Contains the actual files you're working on.

2. **Staging Area (Index)**:  
   - Holds changes before they are committed to the repository.

3. **Local Repository**:  
   - Holds the entire history of the project, including commits, branches, and tags. Stored in the `.git` directory.

4. **Remote Repository**:  
   - A copy of your repository stored on a remote server (e.g., GitHub, GitLab) to share and collaborate with others.

---

### How Git Works Internally (Git Objects):

Git uses a **hashing mechanism** (SHA-1 hashes) to ensure the integrity of your repository. Git objects are stored in a compressed format, and they are uniquely identified by their SHA-1 hash.

- **Commit object**: 
  - Stores metadata like the commit message, timestamp, author, and pointers to the previous commit(s) (if any). This forms the **commit history**.
  
- **Tree object**:
  - Represents directories. A tree object contains pointers to other tree objects (subdirectories) and blob objects (files).
  
- **Blob object**:
  - Stores the actual content of a file. Each file is represented as a blob, and Git stores its contents (not its name or metadata).

- **Tag object**:
  - A tag is a pointer to a commit, usually used to mark release points like "v1.0", "v2.0", etc.

### Git Commands Corresponding to Architecture Components:

- **`git init`**: Initializes a new repository. Creates the `.git` directory where all Git data is stored.
- **`git add`**: Adds changes in the working directory to the staging area (index).
- **`git commit`**: Takes the staged changes and commits them to the local repository, creating a commit object.
- **`git push`**: Pushes local commits to a remote repository.
- **`git pull`**: Fetches changes from a remote repository and merges them into your local repository.

### Summary:

- **Git** is a **distributed version control system** that operates with a local copy of the repository on your machine.
- Git has three main areas of focus: the **working directory**, **staging area**, and the **repository** (which stores commits, branches, and history).
- It uses **Git objects** (commits, trees, blobs, tags) to store data efficiently and securely.
- **Remote repositories** allow multiple users to collaborate by sharing their local changes via pushing and pulling.

Does this help explain Git's architecture clearly? Feel free to ask for more details if anything is unclear!










### 2. **Git and Client-Server Interaction:**
Git itself is not a "client" or "server" in the traditional sense (like a web browser or a database server), but it does involve client-server relationships when you're working with remote repositories.

- When you clone, push, or pull from a **remote repository** (like GitHub), **Git** acts as the **client** communicating with the remote server to retrieve or send data. However, Git doesn't run a server itself; instead, it's the tool that interacts with the server via the Git protocol (typically over SSH or HTTPS).

### 3. **The Remote Repository (Server):**
In this case, a platform like **GitHub**, **GitLab**, or **Bitbucket** acts as the **server** that hosts the repository, while your local machine running Git is the **client** that communicates with that server.

- When you **push** changes, you're sending your local commits from your Git client (your computer) to the remote Git server (GitHub, GitLab, etc.).
- When you **pull** or **clone** a repository, you're downloading the project files and history from the remote server to your local Git client.

### 4. **Metaphor for Git:**
If you want a simple metaphor:  
Think of **Git** as the **tool** you use to manage and organize your project locally. The **client** part comes into play when you're interacting with a **remote repository** (the server) to push or pull changes, but Git itself is not a full-fledged client-server system like a web browser connecting to a web server.

### Git Workflow:
- **Local Git repository** (client) on your machine: You commit, branch, and merge changes.
- **Remote Git repository** (server) on GitHub, GitLab, etc.: You push and pull changes from this centralized location.

### Summary:
- Git is a **distributed version control system**.
- It uses a **client-server model** when interacting with remote repositories, where your local Git (client) interacts with a remote server (GitHub, GitLab, etc.).
- Git itself is not strictly a "client" but can act as one when interacting with remote repositories. 

Does that help clarify things? Feel free to ask for more details if you have further questions!

### 2. **Setting Up Git**
Before you start using Git, you need to set it up on your computer.

- **Install Git**:  
  Download and install Git from [Git’s official website](https://git-scm.com/).

- **Configure Git**:  
  Open a terminal or command prompt and set up your name and email. This information will be associated with your commits.

  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "youremail@example.com"
  ```

### 3. **Creating a Git Repository**
A **repository** is a project folder where Git tracks the changes. You can either create a new repository or clone an existing one.

- **To create a new repository**:
  Navigate to the folder where you want to create your project and run:
  
  ```bash
  git init
  ```
  This will initialize an empty Git repository in that folder.

- **To clone an existing repository**:
  If you're working on a project that's already on a platform like GitHub, you can clone it using:
  
  ```bash
  git clone <repository_url>
  ```
  Example:
  
  ```bash
  git clone https://github.com/username/repository.git
  git archive --output=./example_repo_archive.tar --format=tar HEAD
  ```

```bash
git archive --output=./example_repo_archive.tar.gz --format=tar HEAD ./build
```
A partial archives of the repository can be created by passing a path argument. This example adds a ./build path argument to the archive command. This command will output an archive containing only files stored under the ./build directory

### 4. **Basic Git Commands**

- **Check status of files**:
  To see which files have been changed, added, or deleted, run:
  
  ```bash
  git status
  ```

- **Track new or modified files**:
  When you add new files or modify existing ones, you need to tell Git to "track" them. Use:
  
  ```bash
  git add <file_name>
  ```
  Or add all changed files:
  
  ```bash
  git add .
  ```

- **Commit changes**:
  After staging your changes with `git add`, you need to commit them. A commit is a snapshot of your files at a particular point in time. Always write a meaningful commit message that explains your changes.
  
  ```bash
  git commit -m "Your commit message"
  ```

- **View commit history**:
  To see a history of your commits:
  
  ```bash
  git log
  ```

- **Create branches**:
  Branches allow you to work on different parts of the project without affecting the main project code. You can create a branch with:
  
  ```bash
  git branch <branch_name>
  ```

  Switch to that branch with:
  
  ```bash
  git checkout <branch_name>
  ```

- **Merge branches**:
  Once you've worked on your feature or fix in a branch, you can merge it back into the main branch (usually `main` or `master`). First, switch to the branch you want to merge into (e.g., `main`):

  ```bash
  git checkout main
  ```

  Then, merge the other branch into it:
  
  ```bash
  git merge <branch_name>
  ```

### 5. **Pushing and Pulling Changes**

When you're working with a remote repository (like GitHub), you need to push your changes to share them and pull others' changes.

- **Push changes to remote**:
  After committing your changes locally, you can push them to a remote repository like GitHub:
  
  ```bash
  git push origin <branch_name>
  ```

- **Pull updates from the remote repository**:
  If other people have made changes, you can pull those updates:
  
  ```bash
  git pull origin <branch_name>
  ```

### 6. **Working on a Simple Git Project: A To-Do List App**

Let’s create a basic project to apply Git.

#### Step 1: Initialize the repository
Create a folder called `todo-app`:

```bash
mkdir todo-app
cd todo-app
git init
```

#### Step 2: Create the first version of your app
Let’s create a simple `index.html` file with basic content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To-Do List</title>
</head>
<body>
  <h1>My To-Do List</h1>
  <ul>
    <li>Buy groceries</li>
    <li>Finish Git tutorial</li>
    <li>Clean the house</li>
  </ul>
</body>
</html>
```

#### Step 3: Track and commit changes

1. Add the `index.html` file:
   ```bash
   git add index.html
   ```

2. Commit your changes:
   ```bash
   git commit -m "Initial commit with basic to-do list"
   ```

#### Step 4: Make a change (like adding a new to-do item)
Edit `index.html` to add a new item to the list:

```html
    <li>Start a new project</li>
```

#### Step 5: Track, commit, and push changes

1. Add the changes:
   ```bash
   git add index.html
   ```

2. Commit the update:
   ```bash
   git commit -m "Added new task to the to-do list"
   ```

3. Push the changes to GitHub (make sure you’ve set up a remote repository on GitHub and linked it):

   ```bash
   git remote add origin https://github.com/yourusername/todo-app.git
   git push -u origin main
   ```

---

### Recap of Commands

Here’s a list of the most commonly used Git commands:

1. `git init` – Initialize a new repository.
2. `git add <file>` – Add files to staging.
3. `git commit -m "<message>"` – Commit staged files.
4. `git status` – View file status.
5. `git log` – View commit history.
6. `git branch <branch_name> ` ` git branch -M main  – Create a new branch & rename current branch to main .
7. `git checkout <branch_name>` – Switch branches.
8. `git merge <branch_name>` – Merge another branch into the current one.
9. `git push` – Push commits to a remote repository.
10. `git pull` – Pull changes from a remote repository.

---

### Conclusion

By following these steps, you’ve learned how to create a Git repository, make and commit changes, and collaborate by pushing to and pulling from a remote repository. As you get more comfortable, you can dive into more advanced Git features, but these basics will get you started. Would you like help setting up a remote repository or working on any specific part of this?


# Intermediate git

Sure! Let's dive into intermediate Git concepts and commands. This will help you understand how to work with Git in more advanced ways, including collaboration, branching, rebasing, and more. We'll go through the key topics step by step.

### 1. **Git Branching**

Git branches allow you to work on different parts of a project without affecting the main (or `master`/`main`) branch. This is useful for working on features or fixes separately.

#### Key Commands:
- **Create a new branch:**
  ```bash
  git branch <branch-name>
  ```

- **Switch to another branch:**
  ```bash
  git checkout <branch-name>
  ```

- **Create and switch to a branch in one command:**
  ```bash
  git checkout -b <branch-name>
  ```

- **List all branches:**
  ```bash
  git branch
  ```

- **Delete a branch:**
  ```bash
  git branch -d <branch-name>  # If the branch is fully merged
  git branch -D <branch-name>  # Force delete the branch
  ```

- **Rename a branch:**
  ```bash
  git branch -m <new-branch-name>
  ```

#### Example Workflow:
1. Create a feature branch:
   ```bash
   git checkout -b feature/new-UI
   ```
2. Make your changes and commit them.
3. Switch back to the main branch:
   ```bash
   git checkout main
   ```
4. Merge the feature branch back into `main`:
   ```bash
   git merge feature/new-UI
   ```

### 2. **Staging and Committing Changes**

Intermediate Git also involves managing changes efficiently.

#### Key Commands:
- **Check the status of your repository:**
  ```bash
  git status
  ```

- **Stage a file (add it to the index for the next commit):**
  ```bash
  git add <file-name>
  ```

- **Stage all changes:**
  ```bash
  git add .
  ```

- **Commit changes:**
  ```bash
  git commit -m "Your commit message"
  ```

- **Commit with changes staged but skip files with errors:**
  ```bash
  git commit -a -m "Your commit message"
  ```

- **Amend the last commit:**
  If you forgot to include something in the last commit:
  ```bash
  git commit --amend
  ```

  This opens your default editor to modify the commit message or add changes.

#### Example:
1. Make changes in a file.
2. Stage the file:
   ```bash
   git add index.html
   ```
3. Commit the changes:
   ```bash
   git commit -m "Update header styling"
   ```

### 3. **Working with Remote Repositories**

Most collaborative work happens through remote repositories like GitHub, GitLab, or Bitbucket.

#### Key Commands:
- **Clone a repository:**
  ```bash
  git clone <repository-url>
  ```

- **Check configured remotes:**
  ```bash
  git remote -v
  ```

- **Add a remote:**
  ```bash
  git remote add <remote-name> <repository-url>
  ```

- **Fetch updates from the remote repository:**
  ```bash
  git fetch
  ```

- **Pull updates (fetch + merge):**
  ```bash
  git pull
  ```

- **Push changes to a remote repository:**
  ```bash
  git push origin <branch-name>
  ```

- **Push to a specific remote:**
  ```bash
  git push <remote-name> <branch-name>
  ```

- **Remove a remote:**
  ```bash
  git remote remove <remote-name>
  ```

#### Example:
1. Clone a repository:
   ```bash
   git clone https://github.com/user/repo.git
   ```
2. After working locally, push the changes:
   ```bash
   git push origin feature/new-UI
   ```

### 4. **Rebasing vs Merging**

Both rebasing and merging integrate changes from one branch to another, but they work differently.

#### Merge:
- **Merge** creates a `new commit` that `combines the histories` of two branches.
- **Command:**
  ```bash
  git merge <branch-name>
  git merge --abort  # reverse merginging
  ```

#### Rebase:
- **Rebase** rewrites the commit history by moving the entire branch to begin on top of another branch. This makes the history linear.
- **Command:**
  ```bash
  git rebase <branch-name>
  ```

- **Interactive Rebase:**
  This lets you edit, squash, or reorder commits in a branch.
  ```bash
  git rebase -i <commit-id>
  ```

#### Example Workflow:
1. **Merge**:
   - Start from the `main` branch:
     ```bash
     git checkout main
     ```
   - Merge your feature branch:
     ```bash
     git merge feature/new-UI
     ```

2. **Rebase**:
   - Rebase the `feature/new-UI` branch on top of `main`:
     ```bash
     git checkout feature/new-UI
     git rebase main
     ```

### 5. **Undoing Changes**

Git has a lot of flexibility when it comes to undoing changes.

#### Key Commands:
- **Undo changes in the working directory (before staging):**
  ```bash
  git checkout -- <file-name>
  ```

- **Unstage a staged file:**
  ```bash
  git reset <file-name>
  ```

- **Undo the last commit but keep the changes in the working directory:**
  ```bash
  git reset --soft HEAD~1
  ```

- **Undo the last commit and discard changes (dangerous!):**
  ```bash
  git reset --hard HEAD~1
  ```

### 6. **Git Stash**

Sometimes you may want to switch branches or work on something else without committing your current work. You can stash your changes temporarily.

#### Key Commands:
- **Stash changes:**
  ```bash
  git stash
  ```

- **List stashed changes:**
  ```bash
  git stash list
  ```

- **Apply the most recent stash:**
  ```bash
  git stash apply
  ```

- **Apply a specific stash:**
  ```bash
  git stash apply stash@{n}
  ```

- **Pop a stash (apply and remove from the stash list):**
  ```bash
  git stash pop
  ```

- **Drop a specific stash:**
  ```bash
  git stash drop stash@{n}
  ```

### 7. **Git Tags**

Git tags are used to mark specific points in the repository's history (often used for releases).

#### Key Commands:
- **Create a tag:**
  ```bash
  git tag <tag-name>
  ```

- **Create a lightweight tag (without any extra information):**
  ```bash
  git tag <tag-name> <commit-id>
  ```

- **List tags:**
  ```bash
  git tag
  ```

- **Push tags to remote:**
  ```bash
  git push origin <tag-name>
  ```

- **Delete a tag locally:**
  ```bash
  git tag -d <tag-name>
  ```

- **Delete a tag from remote:**
  ```bash
  git push --delete origin <tag-name>
  ```

---

These are intermediate-level Git topics that will help you work more efficiently with version control, collaborate on projects, and keep a clean and organized history. Let me know if you'd like to dive deeper into any specific area!


# Advance

Great! Now let's dive into **advanced Git** concepts and workflows. These topics will further enhance your understanding of Git, focusing on collaboration, advanced branching, and Git's more powerful features. These will help you manage larger projects, contribute to open-source, and work more efficiently.

### 1. **Advanced Branching Techniques**

Advanced Git branching is useful for managing large teams and complex projects. We'll explore strategies like **Git Flow**, **Feature Branching**, and **Release Management**.

#### **Git Flow Workflow**
Git Flow is a popular branching model that helps to organize your work around feature development, releases, and hotfixes.

**Key Branches:**
- **`main`**: This branch always holds the production-ready code.
- **`develop`**: Integrates all features and is the codebase for the next release.
- **`feature/*`**: Used for new features, created from `develop`.
- **`release/*`**: For preparing a new release (final fixes, versioning).
- **`hotfix/*`**: For quick fixes to production, based on `main`.

**Example Workflow:**
1. Start a new feature:
   ```bash
   git checkout develop
   git checkout -b feature/new-feature
   ```
2. After finishing the feature, merge it back into `develop`:
   ```bash
   git checkout develop
   git merge feature/new-feature
   ```
3. Once `develop` is ready for release, create a release branch:
   ```bash
   git checkout develop
   git checkout -b release/1.0.0
   ```
4. After preparing the release, merge it into both `main` and `develop`:
   ```bash
   git checkout main
   git merge release/1.0.0
   git checkout develop
   git merge release/1.0.0
   ```

**Commands to Set Up Git Flow:**
```bash
git flow init
```

---

### 2. **Rebasing and Advanced Rebase Techniques**

While we've touched on basic rebasing, it’s worth going deeper into **interactive rebase**, which allows you to clean up commit history and modify it.

#### **Interactive Rebase**
Interactive rebasing lets you edit commits, reorder them, squash them, and even delete them.

**Start an interactive rebase:**
```bash
git rebase -i HEAD~n  # n is the number of commits you want to edit (e.g., HEAD~5)
```

**What you can do during an interactive rebase:**
- **Pick**: Keep the commit as is.
- **Reword**: Change the commit message.
- **Edit**: Modify the commit content.
- **Squash**: Combine this commit with the previous one.
- **Fixup**: Similar to squash, but discards the commit message.
- **Drop**: Remove the commit.

#### Example Workflow:
1. Start an interactive rebase:
   ```bash
   git rebase -i HEAD~3
   ```
2. Change `pick` to `squash` for combining commits.
3. Edit the commit message and save.
4. Complete the rebase:
   ```bash
   git rebase --continue
   ```

#### **Rebasing vs Merging:**
- **Rebasing** rewrites history (linear history, cleaner commits).
- **Merging** preserves commit history (useful for preserving the context of the branch).

**Note**: **Never rebase public history** that has already been pushed to shared repositories, as it rewrites history.

---

### 3. **Working with Submodules**

Git submodules allow you to include other Git repositories as a subdirectory within your repository. This is useful for managing dependencies or large monorepos.

#### **Key Commands:**
- **Add a submodule:**
  ```bash
  git submodule add <repository-url> <submodule-directory>
  ```

- **Initialize and clone submodules:**
  If you clone a repository with submodules:
  ```bash
  git submodule init
  git submodule update
  ```

- **Update a submodule:**
  ```bash
  git submodule update --remote
  ```

- **Remove a submodule:**
  ```bash
  git submodule deinit -f <submodule-directory>
  git rm <submodule-directory>
  rm -rf .git/modules/<submodule-directory>
  ```

Submodules can be tricky, so it’s good to be comfortable with how they work for managing dependencies.

---

### 4. **Git Hooks**

Git hooks allow you to automate tasks at key points during the Git lifecycle (before commits, before pushes, etc.). You can use hooks for tasks like running tests before committing, formatting code, or verifying commit messages.

#### **Common Hooks:**
- **`pre-commit`**: Runs before a commit is made.
- **`commit-msg`**: Runs after the commit message is entered but before the commit is finalized.
- **`pre-push`**: Runs before pushing to a remote repository.

#### Example: Set up a `pre-commit` hook to run linting:
1. Create a `pre-commit` file in `.git/hooks/` (if it doesn’t exist):
   ```bash
   touch .git/hooks/pre-commit
   chmod +x .git/hooks/pre-commit
   ```

2. Add a command to lint code before committing:
   ```bash
   #!/bin/sh
   npm run lint  # or your preferred linter
   ```

3. Now every time you commit, the linter will run.

---

### 5. **Squashing Commits**

Squashing commits is useful to combine multiple small, trivial commits into a single commit. This helps clean up the history, especially before merging to `main` or `develop`.

#### **Squash Commits with Interactive Rebase:**
- Run interactive rebase:
  ```bash
  git rebase -i HEAD~n  # where n is the number of commits you want to squash
  ```

- Change `pick` to `squash` or `fixup` for the commits you want to combine.
- Edit the commit message as needed.

---

### 6. **Git Bisect**

Git bisect helps you identify which commit introduced a bug by performing a binary search through your commit history.

#### **Basic Workflow:**
1. Start bisecting:
   ```bash
   git bisect start
   ```

2. Mark the bad commit (where the bug is present):
   ```bash
   git bisect bad
   ```

3. Mark the good commit (where the bug was not present):
   ```bash
   git bisect good <commit-id>
   ```

4. Git will checkout a commit between the good and bad commits. Test the code.
5. Continue the bisect process by marking the commit as `good` or `bad`:
   ```bash
   git bisect good
   git bisect bad
   ```

6. Once you’ve found the commit, end the bisect:
   ```bash
   git bisect reset
   ```

---

### 7. **Git Rebasing with Conflicts**

When rebasing, conflicts might occur. You'll need to resolve them before continuing with the rebase.

#### **Resolving Conflicts:**
1. Git will pause the rebase and tell you which files have conflicts.
2. Manually resolve the conflicts in the affected files.
3. Stage the resolved files:
   ```bash
   git add <file-name>
   ```
4. Continue the rebase:
   ```bash
   git rebase --continue
   ```

If you decide you want to abort the rebase and revert to the original branch state:
```bash
git rebase --abort
```

---

### 8. **Advanced Git Log**

The `git log` command is an essential tool for viewing commit history, and advanced options allow you to format and filter the log.

#### **Common Log Options:**
- **Show the commit history in a graph format:**
  ```bash
  git log --graph --oneline --all
  ```

- **Show commits by a specific author:**
  ```bash
  git log --author="Author Name"
  ```

- **Show commits with a specific message pattern:**
  ```bash
  git log --grep="bug fix"
  ```

- **Show commits between two dates:**
  ```bash
  git log --after="2024-01-01" --before="2024-11-01"
  ```

---

### 9. **Git Reflog**

Git’s `reflog` records changes to the tips of branches and allows you to recover lost commits or branches.

#### **Using Reflog to Recover Lost Commits:**
If you lose a branch or commit, you can view its history with:
```bash
git reflog
```

Then, find the commit ID and checkout the lost commit:
```bash
git checkout <commit-id>
```

You can even create a new branch from the lost commit:
```bash
git checkout -b new-branch <commit-id>
```

---

### Conclusion

Advanced Git gives you the tools to manage complex projects, work with large teams, and maintain a clean and organized history. By mastering features like **rebasing**, **submodules**, **hooks**, and **bisecting**, you can handle nearly any Git-related challenge. Let me know if you'd like to explore any of these topics further!
 


 # PR MR TEMPLATE

 ## Pull Request Title
Provide a concise title summarizing the changes. For example, "Implement search functionality for homepage".
[branch_name] version(build bunber)  e.g.[Realease]1.2.3(4)
## Description
Explain the purpose of this pull request, including:
- The problem it solves or the feature it introduces.
- Relevant issue numbers or links to existing discussions.

## Type of Change
Please mark the relevant option(s):
- [x] Bug fix (fixes a reported issue or defect)  this iswhat i did
- [ ] New feature (adds new functionality without breaking existing features)
- [ ] Breaking change (modifies existing functionality, potentially causing incompatibility)
- [ ] Documentation update (improves or updates project documentation)

## How Has This Been Tested?
Detail your testing approach, including:
- Steps to reproduce or validate the changes.
- Testing environments (e.g., OS, browsers, frameworks).
- Tests conducted (manual, unit, integration, etc.).

## Checklist
Please ensure all items are checked before submitting:
- [ ] I have read and followed the [CONTRIBUTING](LINK_TO_CONTRIBUTING.MD) guidelines.
- [ ] My code adheres to the project’s code style and conventions.
- [ ] I have added or updated tests to cover my changes.
- [ ] My changes do not introduce any breaking functionality.
- [ ] Documentation has been updated to reflect these changes (if needed).
- [ ] I have added relevant comments to the code, particularly for complex logic.

## Screenshots or Visuals
Include screenshots or videos that explain the changes, if applicable.

## Additional Notes
Provide any further information about this pull request, such as:
- Required deployment changes or migrations.
- New dependencies introduced.
- Known issues or limitations.
