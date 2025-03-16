# How to Collaborate on Our GitHub Repository

This guide explains how to work with our GitHub repository. Follow these steps to clone the repo, create your own branch, make changes, and update your local copy after changes are merged to the main branch.

---

## 1. Clone the Repository

Open your terminal and run:

```bash
git clone https://github.com/your-org/your-repository.git
```

_Replace `https://github.com/your-org/your-repository.git` with the actual repository URL._

---

## 2. Create Your Own Branch

To create a new branch and switch to it, use:

```bash
git switch -C feature-branch-name
```

_Replace `feature-branch-name` with a descriptive name for your feature or bugfix._

> **Note:**  
> The `-C` flag force-creates the branch by overwriting any existing local branch with the same name.  
> If you want to create a branch only if it doesn't exist, use `git switch -c feature-branch-name` instead.

---

## 3. Make Changes, Commit, and Push

After making your code changes:

1. **Stage your changes:**

   ```bash
   git add .
   ```

2. **Commit your changes:**

   ```bash
   git commit -m "feature added: [brief description]"
   ```

3. **Push your branch to GitHub and set the upstream:**

   ```bash
   git push -u origin feature-branch-name
   ```

_Replace `feature-branch-name` with your branch name._

---

## 4. Update Your Local Main Branch After Merging

Once your pull request is reviewed and merged into the `main` branch, update your local repository by:

1. **Switch to the main branch:**

   ```bash
   git switch main
   ```

2. **Fetch the latest changes:**

   ```bash
   git fetch
   ```

3. **Pull the latest changes:**

   ```bash
   git pull
   ```

---

## ⚠️ Important Warning: Keeping Your Feature Branch Up-to-Date

**Scenario:**  
Suppose you're working on a feature in your own branch while another feature has been merged into the `main` branch. If you do not update your branch with these latest changes and try to push your work, you might face the following issues:

1. **Merge Conflicts:**

   - **Intern Impact:** When your branch diverges from `main`, you might encounter merge conflicts that require manual resolution before your changes can be merged.
   - **Maintainer Impact:** Unresolved conflicts can lead to integration issues, potentially overwriting or conflicting with other merged changes.

2. **Integration Bugs:**
   - Your feature might be developed on an outdated codebase, which can lead to unexpected behavior or bugs once integrated with the latest code in `main`.

**How to Fix This:**

Before pushing further or opening a pull request, update your branch by incorporating the latest changes from `main`:

### Option 1: Rebase Your Branch

```bash
git fetch origin
git switch feature-branch-name
git rebase origin/main
```

- **Resolve any conflicts** during the rebase (use `git rebase --continue` after resolving).
- This method creates a linear history, which can make your changes easier to review.

### Option 2: Merge `main` into Your Branch

```bash
git fetch origin
git switch feature-branch-name
git merge origin/main
```

- **Resolve any merge conflicts**, then commit the merge.
- This method preserves the branch history, showing when `main` was merged into your branch.

After updating your branch, run all tests to ensure everything integrates properly, then push your changes:

```bash
git push origin feature-branch-name
```

_(If you used rebase, you might need to force-push with `git push -f`—use this carefully and communicate with your team.)_

**Remember:**  
Always update your feature branch regularly with changes from `main` to avoid conflicts and ensure smooth integration. This practice is critical to maintaining a stable codebase and minimizing disruptions for both you and the maintainers.
