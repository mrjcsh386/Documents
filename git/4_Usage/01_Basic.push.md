 ## Summary:
 `git push` is how your local history *leaves your machine and becomes shared
 reality*.

 It sends commits from your local branch to a remote repository, updating the
 remote branch to point at the same commit you have locally. Until you push,
 your work exists only in your private universe.

 ## Examples:
 There are two ways to push to a repository. Both of which, depend on if your
 current local repo has synced to the remote repo + target branch:
 ### 1. First time push for a new branch:
 If you're pushing a new local branch for the first time, use the `-u` flag to
 set upstream tracking branch.
 ```bash
 user@host:~$ git push -u origin main
 ```
 ### 2. Pushing to an already synced repo and branch:
 ```bash
 user@host:~$ git push origin main
 ```
 ### 3. Force push (use with extreme caution):
 This overwrites the remote repositories history with your local history. It is
 generally only safe if you are the only person working on the branch.
 ```bash
 user@host:~$ git push --force-with-lease origin main
 # Or the less safe: git push -f origin main
 ```

 ## Use cases:
 - To save the current committed state as a poor mans backup strategy.
 - To contribute code to a remote repository(potentially shared).

---
 The essential mechanics:
 - `git push` transfers commits not files. The remote reconstructs files from
   commit history.
 - By default, it pushes the current branch to its upstream remote branch.
 - If the remote branch has moved ahead, the push is rejected until you
   reconcile the histories.
 - Authentication and permissions decide whether the push is allowed at all.

 Conceptually, pushing is publication. A commit is a written entry; a push is
 releasing it to the archive where others can read, build, and depend on it.

 Once pushed, your commits influence teammates, automation, and releases.
 `git push` is the moment where responsibility begins, and history stops being
 just yours.
