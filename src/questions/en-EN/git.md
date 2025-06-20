<a href="../../../README.md">← Back</a>

<div align="center">
  <img src="../../../src/assets/icons/icons-for-titles/git.png">
  <h2>GIT</h2>
</div>
<br />

<details>
<summary><span>1. What is <b>Git</b>?</span></summary>
<br />

**Git** is a distributed version control system that allows you to store different versions of code, which can be reverted if needed while working collaboratively.

It records the history of changes, supports parallel work in branches, and ensures convenient code merging.

</details>

---

<details>
<summary><span>2. What states can a file be in?</span></summary>
<br />

In Git, a file can be in the following states:

- **Untracked** — a new file that Git does not know about yet. The file exists in the working directory but has not been added under version control.
- **Tracked** — a file that Git tracks. Tracked files can be in three states:
  - **Unmodified** — the file has not changed since the last commit.
  - **Modified** — the file has been changed but the changes have not been staged for commit yet.
  - **Staged** — the file changes have been added to the index and are ready for commit.

After committing, all staged files transition to the unmodified state.

</details>

---

<details>  
<summary><span>3. How to stage a file?</span></summary>  
<br />

To add a file to the index (**staged** state), use the `git add` command:

- `git add filename.txt` — add a specific file.
- `git add .` — add modified files in the current directory, but **does not include deleted files**.
- `git add --all` / `git add -A` — add **all changes**, including deleted files.
- `git add *.js` — add all files with a specific extension.
- `git add directory/` — add all files from a specific directory.

After executing this command, files will be prepared for the commit.

Additional modes:

- `git add -i` — interactive mode, allowing selective addition of changes.
- `git add -p` — enables staging **only certain parts** (hunks) of a file.

</details>

---

<details>  
<summary><span>4. How to commit changes?</span></summary>  
<br />

To commit changes in Git, use the `git commit` command:

- `git commit -m "message"` — create a commit with the provided message.
- `git commit` — opens a text editor for writing a commit message.
- `git commit -a -m "message"` — automatically stages and commits **only tracked files**, but does not include new (`untracked`) files.

</details>

---

<details>
<summary><span>5. How to clone a repository to a local machine?</span></summary>
<br />

To clone a repository, use the `git clone` command:

- `git clone <url>` — clones the repository into the current directory.
- `git clone <url> <directory>` — clones the repository into the specified directory, **creating it automatically** if it does not exist.

The URL can be either an HTTPS or SSH repository address.

</details>

---

<details>
<summary><span>6. How to push changes to a remote repository?</span></summary>
<br />

To push changes to a remote repository, use the `git push` command:

- `git push origin main` — pushes changes from the local `main` branch to the corresponding remote repository branch (`origin/main`).
- `git push` — pushes changes to the current branch if the remote tracking branch is set.
- `git push -u origin branch-name` — pushes a new branch to the remote repository and sets up tracking.
- `git push --force` — **forcibly overwrites** the remote repository history (**use with caution!**).
- `git push --tags` — pushes tags to the remote repository.

</details>

---

<details>  
<summary><span>7. Why is <b>git push --force</b> dangerous?</span></summary>  
<br />

The **`git push --force`** command forcibly overwrites the remote repository history, **ignoring** changes made by others. This can lead to **loss of their commits** and make recovery difficult.

Instead, use **`git push --force-with-lease`**, which ensures that no new commits have been pushed to the remote branch before forcing the changes. This reduces the risk of losing updates made by other developers.

</details>

---

<details>
<summary><span>8. What is the purpose of the <b>set-upstream</b> command?</span></summary>
<br />

The `git branch --set-upstream-to` (or `-u` for short) command sets up tracking between a local and remote branch. Once configured, you can use **shorter commands** like `git pull` and `git push` without specifying the remote repository name and branch.

</details>

---

<details>
<summary><span>9. What is the difference between <b>git pull</b> and <b>git fetch</b>?</span></summary>
<br />

`git fetch` **retrieves** changes from a remote repository but does **not** apply them to the working copy. `git pull` **retrieves and immediately merges** the changes into the current branch (essentially `git fetch` + `git merge`).

</details>

---

<details>
<summary><span>10. What is a <b>pull-request</b>?</span></summary>
<br />

A **Pull Request (PR)** is a mechanism for proposing changes to a repository. A developer creates a separate branch, makes changes, and requests to merge them into the main branch via PR. This allows **code review, discussion, and safe integration** of changes into the project.

</details>

---

<details>  
<summary><span>11. How can a commit message be formatted?</span></summary>  
<br />

A well-structured commit message should be **clear, concise, and informative**, helping other developers quickly understand the changes. One common approach is **Conventional Commits**, which defines a structured format:

### **Commit types in Conventional Commits:**

- **feat** — adding new functionality
- **fix** — fixing a bug
- **refactor** — improving code without changing functionality
- **docs** — updating documentation
- **style** — formatting changes (e.g., spaces, indentation)
- **test** — adding or modifying tests
- **chore** — technical tasks not affecting code (e.g., updating dependencies)

</details>

---

<details>
<summary><span>12. How to view commit history?</span></summary>
<br />

- `git log` — basic output with full commit details.
- `git log --oneline` — compact output (one line per commit).
- `git log --graph` — visual representation of branches in a graph.
- `git log -p` — shows changes in each commit.
- `git log --author="name"` — filters by author.
- `git log --since="2 weeks ago"` — filters by date.
- `git log <file>` — displays the history of a specific file.

You can also combine options, e.g., `git log --oneline --graph` for a compact branch visualization.

</details>

---

<details>
<summary><span>13. What is <b>HEAD</b>?</span></summary>
<br />

HEAD is a special reference in Git that points to the current commit in the active branch. It acts as a "cursor" indicating where you are in the repository's history.

Key characteristics of HEAD:

- Typically points to the latest commit in the current branch.
- Moves automatically when switching branches.
- Can be **detached** when checking out a specific commit (`detached HEAD`).
- Used in commands such as `git reset HEAD~1` to undo the last commit.

HEAD is like a bookmark in a book—it shows where you are in the project's history.

</details>

---

<details>
<summary><span>14. What is the difference between <b>^</b> and <b>~</b>?</span></summary>
<br />

- **Tilde (`~`)** refers to a commit **N generations back** along the first parent line.
- **Caret (`^`)** specifies **which parent** to refer to (e.g., first or second in a merge commit).

</details>

---

<details>
<summary><span>15. How to check the repository's state?</span></summary>
<br />

The `git status` command shows the current state of the repository:

- Displays the current branch.
- Shows **untracked** files.
- Lists **modified** files.
- Indicates **staged** files (added to the index).
- Displays the repository’s sync state with the remote.

Additional options:

- `git status -s` or `git status --short` — compact output.
- `git status -b` — also shows branch details.
- `git status -u` — displays untracked files inside directories.

</details>

---

<details>
<summary><span>16. How to modify the last commit?</span></summary>
<br />

To modify the last commit, use `git commit --amend`:

- Allows changing the commit message.
- Adds new changes to the last commit.
- Changes the commit author.

</details>

---

<details>
<summary><span>17. How to undo a commit?</span></summary>
<br />

There are several ways to undo a commit:

1. **git reset** — moves HEAD back and cancels commits:

   - `git reset --soft HEAD~1` — cancels the commit but **keeps changes staged**.
   - `git reset --mixed HEAD~1` — cancels the commit and **unstages changes** (default behavior).
   - `git reset --hard HEAD~1` — completely removes the commit **along with all changes**.

2. **git revert** — creates a new commit that **undoes** changes from a previous commit:
   - `git revert HEAD` — reverts the latest commit.
   - `git revert <commit-hash>` — reverts a specific commit.

</details>

---

<details>
<summary><span>18. What is the difference between <b>git reset</b> and <b>git revert</b>?</span></summary>
<br />

- `reset` modifies history by deleting commits.
- `revert` preserves history by adding a new commit, making it safer for collaboration.

</details>

---

<details>
<summary><span>19. How to restore deleted commits?</span></summary>
<br />

Deleted commits can be recovered using `git reflog` and `git reset`:

1. `git reflog` displays the log of all HEAD movements, including deleted commits.
2. Find the hash of the needed commit in the reflog output.
3. Use `git reset --hard <commit-hash>` to restore the state.

</details>

---

<details>
<summary><span>20. How to create a new branch?</span></summary>
<br />

There are several ways to create a new branch:

1. **git branch** — creates a branch but does not switch to it:

   - `git branch <branch-name>` — creates a branch from the current commit.
   - `git branch <branch-name> <commit-hash>` — creates a branch from a specific commit.

2. **git checkout** — creates and switches to the new branch:

   - `git checkout -b <branch-name>` — creates a branch from the current commit and switches to it.
   - `git checkout -b <branch-name> <commit-hash>` — creates a branch from a specific commit.

3. **git switch** (Git 2.23+) — a modern alternative to `checkout`:
   - `git switch -c <branch-name>` — creates and switches to a new branch.
   - `git switch -c <branch-name> <commit-hash>` — creates a branch from a specific commit.

</details>

---

<details>
<summary><span>21. How to transfer commits from one branch to another?</span></summary>
<br />

1. **git cherry-pick** — copies individual commits:

   ```bash
   git cherry-pick <commit-hash>
   ```

2. **git merge** — merges branches, transferring all commits:

   ```bash
   git checkout target-branch
   git merge source-branch
   ```

3. **git rebase** — moves commits while rewriting history:
   ```bash
   git checkout feature-branch
   git rebase main
   ```

</details>

---

<details>
<summary><span>22. What is the difference between <b>rebase</b> and <b>merge</b>?</span></summary>
<br />

1. **git merge** — creates a new merge commit, preserving both branch histories.
2. **git rebase** — rewrites history to make it linear but modifies commit hashes.

</details>

---

<details>
<summary><span>23. What problems can arise when using <b>git rebase</b>?</span></summary>
<br />

1. **Merge conflicts** — rebase may generate conflicts that must be resolved manually for each commit.

2. **History modification** — rebase rewrites commit history, which can cause problems in teamwork:

   - Commit hashes change.
   - Tracking changes becomes more complex.
   - Issues may arise during `push`, requiring `force push`.

3. **Rollback difficulties** — rewritten history makes undoing changes harder.

4. **Issues with long branches** — the more commits rebased, the higher the chance of conflicts.

5. **Risk of data loss** — incorrect use of `force push` after `rebase` can erase other developers' changes.

</details>

---

<details>
<summary><span>24. What is stored in the <b>objects</b> folder?</span></summary>
<br />

The **`objects`** folder inside `.git` contains all Git objects — the **foundation of repository history**.

It stores **all commits, files, trees, and tags**, compressed using the zlib algorithm, with names based on **SHA-1 hashes**.

### Object types:

- **Blob** — stores file contents.
- **Tree** — represents directory structure, linking blobs and other trees.
- **Commit** — records changes, referencing a tree and parent commits.
- **Tag** — annotated tags, commonly used for version releases.

**Git does not store files directly** — it saves **snapshots of states**, and all objects reside in `.git/objects`.

</details>

---

<details>
<summary><span>25. What does the <b>git cat-file</b> command do?</span></summary>
<br />

The **`git cat-file`** command allows viewing the contents, type, and size of Git objects (blob, tree, commit, tag) using their SHA-1 hash.

</details>

---

<details>
<summary><span>26. What does the <b>git show</b> command do?</span></summary>
<br />

The **`git show`** command displays detailed information about a commit, including author, date, file changes, and the `diff` between the current and previous version.

</details>

---

<details>
<summary><span>27. What are <b>tags</b> used for?</span></summary>
<br />

**Tags in Git** create markers on important commits, most often used for versioning or releases. They simplify navigation and help quickly switch to significant points in project history.

</details>

---

<details>
<summary><span>28. How does garbage collection work when running <b>git gc</b>?</span></summary>
<br />

In Git, garbage collection (`git gc`) is based on the concept of **reachability**:

- **Reachable objects** (commits, trees, blobs) — objects that have references (HEAD, branches, tags).
- **Unreachable objects** — objects without references that are no longer part of the repository’s history.

`git gc` deletes **unreachable objects** if they have been stored beyond a certain retention period.

</details>

---

<details>
<summary><span>28. What is <b>git stash</b> used for?</span></summary>
<br />

**Git stash** allows you to temporarily save uncommitted changes and return the working directory to a "clean" state. This is useful when you need to:

- Quickly switch to another branch without committing
- Put aside current changes to work on an urgent task
- Save modifications that are not yet ready for a commit

Saved changes can later be restored using `git stash pop` or `git stash apply`.

</details>

---

<details>
<summary><span>29. What does the <b>git clean</b> command do?</span></summary>
<br />

The **`git clean`** command removes untracked files from the working directory. This includes:

- New files that have not yet been added to the index
- Files created during project builds
- Temporary files

### Key options:

- `-n` (--dry-run) — shows which files would be deleted without actually removing them
- `-f` (--force) — forces file deletion
- `-d` — also removes untracked directories
- `-x` — removes ignored files (those listed in `.gitignore`)

⚠️ **Deleted files cannot be recovered!**

</details>

---

<details>
<summary><span>30. What branching strategies do you know?</span></summary>
<br />

1. Git Flow
2. Trunk-Based

</details>

---

<details>
<summary><span>31. How does development proceed in <b>Git Flow</b>?</span></summary>
<br />

**Git Flow** is a branching model with two primary branches:

- **master/main** — the stable production version
- **develop** — the development branch

And three auxiliary branches:

- **feature/** — for new features (branched from `develop`)
- **hotfix/** — for urgent fixes (branched from `master`)
- **release/** — for preparing releases (branched from `develop`)

### Process:

1. Development takes place in feature branches
2. Completed features are merged into `develop`
3. A release branch is created for final testing
4. The release is merged into both `master` and `develop` after testing

</details>

---

<details>
<summary><span>32. How does development proceed in <b>Trunk-Based</b>?</span></summary>
<br />

**Trunk-Based Development** is a branching approach where development is primarily done in the main branch (`trunk/master/main`).

### **Key principles:**

- All developers commit directly to `master`
- Feature branches are **short-lived** (1-2 days)
- Frequent commits with small changes
- Continuous integration (CI) ensures stability
- Feature Toggles allow enabling/disabling unfinished functionality

### **Advantages:**

- Fast code integration
- Fewer merge conflicts
- Easier code maintenance
- Accelerated release cycles

This method is well-suited for **small teams and frequent releases**.

</details>

---

<!-- <details>
<summary><span></span></summary>
<br />


</details>

--- -->
