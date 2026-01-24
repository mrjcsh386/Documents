 ## Summary:
 `git commit` is the act of *making time stick*.

 It takes whatever is in the staging area and records it as a new snapshot in
 the repository's history. After this point, those changes are no longer just
 edits on disk; they are part of the project's timeline.

 ## Example:
 ```bash 
 user@host:~$ git commit -m "Add initial documentation"
 ```

 ## Use cases:
 - Save a snapshot of changes.
 - Track history for individual features.
---
 A few core truths that clarify its role:
 - As it is true with `git add`, `git commit` operates under the context of the
   working `branch` you are executing the commands under (pay sharp attention).
 - `git commit` only sees the staging area. If something wasn't added, it
   doesn't exist as far as the commit is concerned.
 - Each commit has an identity: a hash, an author, a timestamp, and a message.
   Together, these form a durable historical record.
 - Commits are immutable in spirit. You can rewrite history, but that is a
   conscious act, not an accident.
 - A commit represents intent. Ideally, it answers one question: "What changed,
   and why?"

 Conceptually, a commit is a snapshot, not a diff. Git stores differences to
 save space, but your mental model should be "the project looked exactly like
 this at this moment."

 If `git add` is choosing what belongs, `git commit` is sealing it in wax and
 filing it in the archive. From there, branches can diverge, merges can
 reconcile, and history can be read like a technical diary rather than a crime
 scene.
