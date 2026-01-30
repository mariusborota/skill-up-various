# Git Workflow - Detailed State Explanations

### State 0: Null State (Uninitialized Directory)
This is the starting point where the directory is just a simple folder on your drive. 
* **git status**: Used here to verify that no repository exists; it should return a "fatal" error.
* **.gitignore**: It is best practice to create this early to ensure local configuration or Azure-specific temporary files are never tracked.

### State 1: Allocation & Verification
This state officially brings Git into your project lifecycle.
* **git init**: Initializes a new, empty local repository.
* **git clone**: Downloads an existing repository along with its entire history from GitHub.
* **git remote -v**: Serves as a quality check to confirm your local repo is correctly linked to the remote server.

### State 2: Branching
Branching allows you to work on new features (like Azure integration) without affecting the stable `main` code.
* **git switch -c**: The modern command to create a new branch and move into it immediately.
* **Isolation**: Ensures that if something goes wrong, the primary version of your project remains safe.

### State 3 & 4: Staging & Committing
These states represent the "packaging" of your work.
* **Staging (git add)**: The triage area where you select which changes are ready to be saved.
* **Committing (git commit)**: Creates a permanent snapshot in your local history with a descriptive message.

### State 5 & 6: Synchronization & Integration
This moves your local work to the cloud (GitHub).
* **Pushing**: Sends your commits to the remote server.
* **Pull Request (PR)**: The formal process on GitHub to review and merge your feature branch into the `main` branch.
* **Pulling**: Keeps your local machine up to date with changes made by others or finalized PRs.

### State 7: Housekeeping
Maintaining a clean repository is essential for long-term project health.
* **Cleanup**: Deleting local branches that have already been merged to prevent clutter in your environment.

---

## Undo & Error Handling Scenarios

### Scenario 1: Unstage (git restore --staged)
* **Use Case**: You added a file by mistake using `git add` but haven't committed it yet.
* **Effect**: Removes the file from the staging area but keeps your code changes intact.

### Scenario 2: Undo Local Commit (git reset)
* **Soft Reset**: Cancels the commit but keeps your work in the staging area (ideal for fixing a typo in the code).
* **Hard Reset**: Deletes the commit and all work associated with it (use with extreme caution!).

### Scenario 3: Undo Public Push (git revert)
* **Use Case**: You pushed code to GitHub and discovered a bug that needs to be rolled back.
* **Effect**: Creates a new "inverse" commit that cancels out the mistake without deleting the history, making it safe for collaboration.