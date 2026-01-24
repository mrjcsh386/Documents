 ## Summary:
   `git add` is the moment where chaos becomes *potential order*.

   In plain terms: it takes changes from your working directory and places them
 into the staging area (also called the index). Nothing is committed yet. You
 are just saying, "These exact changes are candidates for the next snapshot."

 ## Example:
 ```bash 
 user@host:~$ git add file.txt
 user@host:~$ git add *.md
 ```
 ## Use cases:
 - Stage a single file for commit
 - Stage multiple files using patterns
---
 A few important nuances that matter more than most will admit:
 - `git add` is selective. You can stage a whole file, a directory, or even
   specific lines. This is why Git feels precise rather than blunt.
 - Staging is not automatic. Editing a file does not mean it will be committed.
   Only what you explicitly add is included.
 - You can run `git add` multiple times before a commit. Each run updates the
   staging area to reflect your intent at that moment.
 - `git add` does not record history. It prepares history.
 - `git add` operates within the context of the current `branch`

 Mentally, think of it like a librarians cart. Files on your desk are messy
 reality. The cart holds only the books you've decided belong in the next
 catalog entry. `git commit` is when the catalog entry is actually written.

 This separation is one of Git's superpowers: it lets you shape commits as
 deliberate units of meaning, rather than dumping everyting you touched into
 history.
