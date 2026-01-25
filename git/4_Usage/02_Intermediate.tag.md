 ## Summary:
 `git tag` is how you *name a moment in history*.

 It attaches a meaningful label to a specific commit, without changing the
 commit itself. The code stays the same; your understanding of it becomes
 sharper.

 ## Example:
 1. List Tags
 To view existing tags in your repository:
 ```bash
 user@host:~$ git tag
 v0.0.1a
 v0.1.0a
 v0.1.1a
 ```
 To search for tags that match a specific pattern:
 ```bash
 user@host:~$ git tag -l "*-rc*"
 v1.0.0e-rc
 ```
 ### 2. Create Tags
 By default, tags are created for the commit that your `HEAD` is currently
 pointing to.
 - **Annotated Tag** (Recommended): Use the `-a` option and a message (`-m`).
   This creates a full object with the tagger's name, email, and date.
   ```bash
   user@host:~$ git tag -a v1.4.0e -m "Release version 1.4
   > Comment: This release has that special property that makes me smile."
   ```
   If you omit the `-m` flag, Git will open your default text editor to prompt
   for a message.

 - **Lightweight Tag**: Omit the `-a`, `-s`, or `-m` options. This is just a
   pointer or bookmark to a commit.
   ```bash
   user@host:~$ git tag v1.4-lw
   ```
 - **Tag an Older Commit**: You can tag a specific commit by specifying its
   checksum (SHA) at the end of the command. Use `git log --pretty=oneline`
   to find the commit hash.
   ```bash
   user@host:~$ git tag -a v1.2 <commit-sha> -m "Version 1.2"
   ```
 ### 3. Delete Tags
 - Delete a tag locally:
   ```bash
   user@host:~$ git tag -d <tagname>
   ```
 ## Use cases:
 - To identify key commits as special.
 - To add notation of features included that may have impact.

---
 The essential ideas:
 - A tag points to a commit. It dos not move as history grows, unless you
   deliberately force it to.
 - Tags are usually used for releases, milestones, or reference points you
   want to return to with certainty.
 - Lightweight tags are just names. Annotated tags are objects: they carry a
   message, an author, and a date.
 - Tags do not affect branching or merging. They are markers, not paths.

 Conceptually, branches are like bookmarks you keep reading from, while tags
 are sticky notes saying, "This page mattered." You don't continue writing from
 a tag; you recognize it.

 In a well-kept repository, tags turn raw commit hashes into a map of intent:
 v1.0, v2.1-rc1, stable-2026-01. They are how history becomes navigable, not
 just accurate.
