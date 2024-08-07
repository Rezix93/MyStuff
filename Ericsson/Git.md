### 1. **Sign an ECA:**
Create an account with the Eclipse Foundation if you have not already done so;
Sign a ECA.
Log into the Eclipse Contributor Agreement page;
Complete the form.
An Eclipse Account will grant you access to Gerrit, Bugzilla, and other Eclipse Foundation web resources.
Use the same account to contribute to Eclipse, LocationTech, and PolarSys projects.


### 2. **Create a Token:**
   - Click on `Personal access tokens` and then `Tokens (classic)`.
   - Click `Generate new token`.
   - Give your token a descriptive name and select the necessary scopes. At a minimum, you need `repo` access to push code to a repository.
   - Click `Generate token`.
   - **Copy the token**
   - To avoid being prompted for your PAT every time, you can store your credentials securely using a credential helper.
  ```bash
  git config --global credential.helper cache
  ```

### 3. **REMOTE Trace Compass:**

1. Go to [https://github.com/eclipse-tracecompass/org.eclipse.tracecompass] and Fork it
2. Clone using the web URL. For example :
```
git remote add `github_custom_name` https://github.com/Rezix93/org.eclipse.tracecompass.git
```
### 4. **Adding a Remote:**

To add your forked repository as a remote with a custom name:

```bash
git remote add `github_custom_name` https://github.com/Rezix93/org.eclipse.tracecompass.git
```
In my case: github_custom_name = rezaGithub

### 5. **Verify the Remote:**
To confirm that the remote was added correctly, list all configured remotes:

```bash
git remote -v
```

### 6. **Now time for Github:**
```
~/research$ cd org.eclipse.tracecompass
```

```
cat .git/config 
git config --global user.email "reza.rouhghalandari@ericsson.com"
git config "user.name" "Reza Rouhghalandari"
```
```
Git staus
```


### 7. **`Get update`**

```
git fetch --all
```
```
git rebase origin/master counterAspectChanges 
```
```
git rebase rezaGithub/master 
```


This command fetches all the branches from all the remotes configured for your repository. It updates your local copy of the remote branches without merging the changes into your local branches. It's useful to see what changes have been made in all remotes.

### 8. **`Get git status`**

```
git status
```

This command shows the status of your working directory and the staging area. It lets you see which changes have been staged, which haven't, and which files aren't being tracked by Git. It's a good practice to use `git status` before making commits to see what changes you're about to include.

### 9. **`Create a new branch`**

```
git branch USTvalidate
```

This command creates a new branch named `USTvalidate` from your current branch. Branches in Git are used to isolate development work without affecting other branches in the repository. This command does not switch to the new branch; it only creates it.

### 10. **`Go to new branch`**

```
git checkout USTvalidate
```

This command switches your working directory to the branch named `USTvalidate`. Any new commits you make will now be on this branch. If `USTvalidate` does not exist yet, this command would also create the branch and switch to it.


### 11. **First Add:**

Choose what you want to add from the changes. For example you want to change 3 files: 

```
git add ctf/org.eclipse.tracecompass.tmf.ctf.core/src/org/eclipse/tracecompass/tmf/ctf/core/trace/CtfTmfTrace.java
tmf/org.eclipse.tracecompass.tmf.ui/src/org/eclipse/tracecompass/tmf/ui/project/model/TmfTraceElement.java 
lttng/org.eclipse.tracecompass.lttng2.ust.core/src/org/eclipse/tracecompass/lttng2/ust/core/trace/LttngUstTrace.java -p 
```

### 12. **Then Commit:**

```
git commit -s
```
`-s` means something like this: `Signed-off-by: Your Name <your-email@example.com>`

``` 
git commit -s --amend
```
The --amend option allows you to modify the most recent commit. This is useful if you need to correct the commit message, add changes that were missed, or include the sign-off if it was omitted initially.




### 13. **`Push changes`**

```
git push rezaGithub USTvalidate
```

This command pushes the `USTvalidate` branch to the `rezaGithub` remote repository. The `rezaGithub` remote points to your fork of the 



# After the First Time: 

1. Go to your git directory
2. git fetch --all
3. Add
4. Commit
5. status
6. branch
7. checkout
8. push
9. pull request

# Hint in general: 

```
git checkout -b new-branch-name
git branch
git diff
git add file.name
git commit -m -s
git push rezaGithub new-branch-name
```


After reveiw and change: 
```
cd org.eclipse.tracecompass
git status 
git add analysis/org.eclipse.tracecompass.analysis.counters.core/src/org/eclipse/tracecompass/analysis/counters/core/aspects/ITmfCounterAspect.java
git commit -s --amend
git push rezaGithub new-branch-name -f
```
