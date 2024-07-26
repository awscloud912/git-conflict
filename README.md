# Scenario

Assume two developers are working on the same file in different branches and make conflicting changes.

- **Developer A** is working on the `main` branch.
- **Developer B** is working on the `feature` branch.

1. **Create the Repository and File**
```sh
mkdir git-conflict-example
cd git-conflict-example
git init
echo "Line 1" > file.txt
git add file.txt
git commit -m "Initial commit"
```

2.**Create and Switch to the Feature Branch**
```sh
git checkout -b feature
```

3.**Developer B Makes Changes on the Feature Branch**
```sh
echo "Line 2 from feature branch" >> file.txt
git add file.txt
git commit -m "Add line from feature branch"
```

4.**Switch Back to Main Branch**
```sh
git checkout main
```

5.**Developer A Makes Changes on the Main Branch**
```sh
echo "Line 2 from main branch" >> file.txt
git add file.txt
git commit -m "Add line from main branch"
```
# Conflict Scenario
Now, Developer A wants to merge the feature branch into main.
6.**Merge the Feature Branch into Main**
```sh
git merge feature
```

# Conflict Occurrence
When running the merge command, Git will produce a conflict because both branches made changes to the same line in file.txt.

# Conflict Resolution

1.**Check the Status**
```sh
git status
```
Output will indicate there is a merge conflict:
```sh
On branch main
You have unmerged paths.
...
both modified:   file.txt
```

2.**View & Open the Conflicted File**
cat file.txt
vi file1.txt
The file will look like this:

```sh
Line 1
<<<<<<< HEAD
Line 2 from main branch
=======
Line 2 from feature branch
>>>>>>> feature
```

3.**Resolve the Conflict Manually**
Edit the file to resolve the conflict. You can decide which changes to keep or combine both changes. For example, you can edit the file to:
```sh
Line 1
Line 2 from main branch
Line 2 from feature branch
```

4.**Add the Resolved File**
```sh
git add file.txt
```

5.**Complete the Merge**
```sh
git commit -m "Resolved merge conflict between main and feature branch"
```


# Summary
- **Developer A and Developer B made conflicting changes in different branches.**
- **When attempting to merge, a conflict was detected.**
- **The conflict was resolved manually by editing the file, staging the resolved file, and completing the merge with a commit.**

# Full Example Workflow
1. Initial setup
mkdir git-conflict-example
cd git-conflict-example
git init
echo "Line 1" > file.txt
git add file.txt
git commit -m "Initial commit"

2.Create and switch to feature branch
git checkout -b feature

3. Developer B's changes
echo "Line 2 from feature branch" >> file.txt
git add file.txt
git commit -m "Add line from feature branch"

4. Switch back to main branch
git checkout main

5. Developer A's changes
echo "Line 2 from main branch" >> file.txt
git add file.txt
git commit -m "Add line from main branch"

6. Attempt to merge feature branch into main
git merge feature

7. Resolve conflict
 Edit file.txt to:
# Line 1
# Line 2 from main branch
# Line 2 from feature branch
git add file.txt
git commit -m "Resolved merge conflict between main and feature branch"