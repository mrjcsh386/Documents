 ## Summary:
 `git rebase` is how you *rewrite the path you took without changing where
 you end up*.

 It takes a sequence of commits and reapplies them onto a new base commit,
 creating a cleaner, more linear history. The code result may look the same,
 but the story of how you got there is edited.

 Example:
 ```bash 
 user@host:~$ git checkout feature
 user@host:~$ git rebase main
 ```

 Use cases:
 - Incorporate upstream changes without merge commits
 - Maintain a linear commit history

---
 The facts that keep it grounded:
 - Rebase moves commits by recreating them. New hashes are made; old ones
   are left behind.
 - It is usually used to place your work on top of the latest version of
   another branch, often `main`.
 - Conflicts are resolved one commit at a time, in the order they originally
   happened.
 - Rebasing changes history, which is safe on private branches but dangerous
   on shared ones.

 | Caution: 'rebase' has caused deep offence by way of
 |   clobbering commit history found using 'log' with
 |   the source history of the branch rebase is using
 |   to effectively rebuild the destination branch.

 | Note: I have ranked this as 'advanced' due to the
 |   historically derisive affect on the communities
 |   that have been robbed of credit. Choose 'merge' if
 |   you haven't grasped 'rebase's full impact when
 |   managing a community supported repo.
