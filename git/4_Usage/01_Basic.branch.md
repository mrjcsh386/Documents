 ## Summary:
 `git branch` is how Git lets you *hold multiple futures at once*.

 It manages named pointers to commits, each representing a line of development.
 Creating branches does not copy files or history; it simply gives a new name to
 a particular commit so work can continue without disturbing others. 

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
 - Logically divide features, developers, or to keep experimentation from
   polluting the code base.

---
 The key facts that matter:
 - A branch is a movable pointer. As you commit, the branch advances.
 - `HEAD` marks the branch you are currently on. Your commits follow it like
   ducklings.
 - Creating a branch is cheap and instant. Switching branches changes what
   your working directory looks like.
 - Deleting a branch removes the name, not the history. Commits remain if they
   are reachable elsewhere.

 Conceptually, branches are parallel narratives. One might be "main," another
 "experiments," another "fix-the-thing-that-woke-you-at-3am." `git branch` lets
 you list them, create them, rename them, and prune them, keeping history
 flexible without becoming tangled.

 Used well, branching turns fear into freedom: you can explore, repair, and
 refine without endangering the story already written.
