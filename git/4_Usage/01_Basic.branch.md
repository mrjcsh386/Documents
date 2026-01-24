## Summary:
   A branch is a named pointer to a specific commit, representing an independant
 line of history. Switching branches replaces the working directory with the
 snapshot stored at that pointer. Branches do not affect one another unless
 explicitly joined through merge, rebase, or similar operations. Commits always
 attach to the branch currently checked out, and uncommitted changes belong to
 the working tree, not to any branch, until recorded.

## Example:
   ```bash
     # To see all branches. Will also highlight the one you're using.
     user@host:~$ git branch
     main
     release
     dev/user0
    *dev/user1
   ```
   This answers one question and one question only:
   *Which timelines exit, and which one am I standing in?*

   ```bash
     # Creates a branch without switching to it.
     user@host:~$ git branch arbitrary-aardvark
   ```
   This creates a new branch taking the state of the current working branch
 withouth switching to it.

 ### Deleting a branch
   ```bash
     # To delete a branch.
     user@host:~$ git branch -d arbitrary-aardvark
     # This works if the branch you're deleting has no unmerged
     # material and executed in the branch you've merged it to.

     # To delete a branch with spice.
     user@host:~$ git branch -D arbitrary-aardvark
     # This deletes forcefully. No consideration to what lays
     # beneath!
   ```
 ### Renaming a branch
   ```bash
   user@host:~$ git branch -m dev/user0 dev/luser0
   ```
 ### Enumerating where commits end up.
 Some archilogical digs you are going to undergo, you'll benefit from being able
 locate where commits get stitched into the repositories internal map of reality
 ```bash
 user@host:~$ git branch --contains <commit hash>
 ```

 ## Use cases:
