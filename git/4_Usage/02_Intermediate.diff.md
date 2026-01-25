 ## Summary:
 `git diff` is how Git shows you *difference before consequence*.

 It compares states: what you have now versus what you had before(commit to
 commit), or what you've prepared versus what you've recorded(branch to branch).
 Nothing changes when you run it. It only reveals.

 ## Example:
 The following use of `git diff` shows current working state against last
 recorded `git commit`.
 ```bash
 user@host:~$ git diff
 diff --git a/git/4_Usage/02_Intermediate.diff.md b/git/4_Usage/02_Intermediate.diff.md
 index 445d884..9f7415b 100644
 --- a/git/4_Usage/02_Intermediate.diff.md
 +++ b/git/4_Usage/02_Intermediate.diff.md
 @@ -1,11 +1,50 @@
 -Summary:
 + ## Summary:
 + `git diff` is how Git shows you *difference before consequence*.
 
 -   Uses '/usr/bin/diff' like behaviour against two
 - listed branches.
 + It compares states: what you have now versus what you had before(commit to
 + commit), or what you've prepared versus what you've recorded(branch to branch).
 + Nothing changes when you run it. It only reveals.
  
 - Example: TODO: Generate demonstratable output.
 + ## Example:
 +
 + user@host:~$ git diff authors/mrjcsh386 stage
 + diff --git a/git/4_Usage/02_Intermediate.diff.md b/git/4_Usage/02_Intermediate.diff.txt
 + similarity index 91%
 + rename from git/4_Usage/02_Intermediate.diff.md
 + rename to git/4_Usage/02_Intermediate.diff.txt
 + index 445d884..e6fbd17 100644
 + --- a/git/4_Usage/02_Intermediate.diff.md
 + +++ b/git/4_Usage/02_Intermediate.diff.txt
 + @@ -8,4 +8,4 @@ Summary:
 +   Use cases:
 +   - Verify between two branches pre- and post-merge to
 +     ensure success, or verify differences without
 + -   intending a merge.
 + +   intending a merge.
 + \ No newline at end of file
 +
 
 - Use cases:
 + ## Use cases:
   - Verify between two branches pre- and post-merge to
     ensure success, or verify differences without
     intending a merge.
 +
 +---
 + The important mental anchors:
 + - By default, `git diff` compares your working directory to the staging area.
 +   It answers: "What have I changed that I haven't staged yet?"
 + - With options, it can compare staged changes to the last commit, or any two
 +   commits, branches, or files.
 + - The output is a patch, not a judgment. Lines prefixed with `+` and `-` show
 +   additions and removals, but Git is not telling you what is right--only what
 +   is different.
 + - `git diff` is safe and reversible because it does not act on history or
 +   state. It is pure observation.
 +
 + Think of it as holding two transparencies up to the light and seeing where the
 + ink doesn't line up. Before you decide what to add, commit, split, or discard,
 + `git diff` lets you *see the shape of your change*.
 +
 + In practice, disciplined use of `git diff` is what keeps commits small,
 + intentional, and readable. It is the microscope you use before deciding what
 + belongs in the fossil record.
 ``` 
 The following, is an example of comparing branches.
 ```bash
 user@host:~$ git diff authors/mrjcsh386 stage
 diff --git a/git/4_Usage/02_Intermediate.diff.md b/git/4_Usage/02_Intermediate.diff.txt
 similarity index 91%
 rename from git/4_Usage/02_Intermediate.diff.md
 rename to git/4_Usage/02_Intermediate.diff.txt
 index 445d884..e6fbd17 100644
 --- a/git/4_Usage/02_Intermediate.diff.md
 +++ b/git/4_Usage/02_Intermediate.diff.txt
 @@ -8,4 +8,4 @@ Summary:
   Use cases:
   - Verify between two branches pre- and post-merge to
     ensure success, or verify differences without
 -   intending a merge.
 +   intending a merge.
 \ No newline at end of file
 ```

 ## Use cases:
 - Verify between two branches pre- and post-merge to
   ensure success, or verify differences without
   intending a merge.

---
 The important mental anchors:
 - By default, `git diff` compares your working directory to the staging area.
   It answers: "What have I changed that I haven't staged yet?"
 - With options, it can compare staged changes to the last commit, or any two
   commits, branches, or files.
 - The output is a patch, not a judgment. Lines prefixed with `+` and `-` show
   additions and removals, but Git is not telling you what is right--only what
   is different.
 - `git diff` is safe and reversible because it does not act on history or
   state. It is pure observation.

 Think of it as holding two transparencies up to the light and seeing where the
 ink doesn't line up. Before you decide what to add, commit, split, or discard,
 `git diff` lets you *see the shape of your change*.

 In practice, disciplined use of `git diff` is what keeps commits small,
 intentional, and readable. It is the microscope you use before deciding what
 belongs in the fossil record.
