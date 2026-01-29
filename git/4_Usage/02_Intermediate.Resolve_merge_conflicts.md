 ## Summary:
   Merge conflicts happen when Git cannot automatically combine changes.
 Git's primary job is to maintain historical records of changes, not to
 interpret intent or project state. When that happens, the options below
 show practical ways to resolve a conflict.

 ## Example:
 ### Case A: You are in a merge conflict right now, and you want `branch_b`'s version to win for one file.
 From the `branch_a` branch (or while the merge is paused), do:
 ```bash
 user@host:~$ git restore --source=branch_b -- path/to/workspace.json
 user@host:~$ git add path/to/workspace.json
 ```
 Then continue resolving other conflicts (if any), and finish the merge:
 ```bash
 user@host:~$ git commit
 ```
 In addition to the above, you can use the older form:
 ```bash
 user@host:~$ git checkout active -- path/to/workspace.json
 user@host:~$ git add path/to/workspace.json
 ```
 This is the cleanest way to overwrite the file with the other branch's version.

 ### Case B: You are in a merge conflict and you want "ours" or "theirs" (Git's built-in merge sides)
 During a conflict, Git offers shortcuts:
 ```bash
 # Keep `main`'s (or, the branch you're in) side:
 user@host:~$ git checkout --ours -- path/to/workspace.json
 # Keep `branch_b`'s (or, the other branch) side:
 user@host:~$ git checkout --theirs -- path/to/workspace.json

 user@host:~$ git add path/to/workspace.json
 ```
 Important: in a merge into `main`, "ours" usually means `main`, and "theirs"
 means the branch you are merging in. If you merged `branch_b` into `main`, then
 `--theirs` is likely `branch_b`.

 If you're not 100% sure, prefer the explicit source form in Case A.

 ### Case C: You explicitly want a patch file (diff) and apply it to main.
 This is more fiddly, but doable.
 1. Make a patch for just the file, comparing `main..branch_b`:
 ```bash
 user@host:~$ git diff main..branch_b -- path/to/workspace.json > /tmp/ws.patch
 ```
 2. Switch to `main` (or stay there), and apply:
 ```bash
 user@host:~$ git switch main
 user@host:~$ git apply /tmp/ws.patch
 user@host:~$ git add path/to/workspace.json
 user@host:~$ git commit -m "Apply workspace.json changes from branch_b"
 ```
> Notes:
> - `git apply` does not create a commit; it just edits your working tree.
> - If the file has drifted so the patch doesn't apply cleanly, you can try:
>   1. `git apply --3way /tmp/ws.patch` (attempt a 3-way apply), or
>   2. abandon patching and use Case A (replace file from `branch_b`).

 ## Quick "show me the exact changes for that one file"
 ```bash
 user@host:~$ git diff main..branch_b -- path/to/workspace.json
 ```
 Or a summary:
 ```bash
 user@host:~$ git diff --stat main..branch_b -- path/to/workspace.json
 ```
