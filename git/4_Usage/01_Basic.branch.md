## Summary:
   Branches are for logical spacing of textual and sometimes binary files. It
 is supposed to assist in provisioning a naming schema for a freeze frame of
 time related to code state. This can contribute to political structures,
 features, and to differentiate between code used by 'customers', and code being
 developed.

## Example:
   ```bash
     # To see all branches. Will also highlight the one you're using.
     user@host:~$ git branch

     # Creates a branch without switching to it.
     user@host:~$ git branch arbitrary-aardvark

     # To delete a branch.
     user@host:~$ git branch -d arbitrary-aardvark
     # This works if the branch you're deleting has no unmerged
     # material and executed in the branch you've merged it to.

     # To delete a branch with spice.
     user@host:~$ git branch -D arbitrary-aardvark
     # This deletes forcefully. No consideration to what lays
     # beneath!
   ```
## Use cases:


