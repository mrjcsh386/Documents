 ## Summary:

   Initializes a new Git repository in the current directory or reinitializes
 an existing one. This is typically the first command run in a new project.

 ## Example:
 To initialise a repo locally without the intent of collaborating with
 others, the canonical way to start a repo with sparse hooks that give way
 to a single user, issue the following:
 ```bash
 user@host:~$ git init my_project
 Initialized empty Git repository in /home/user/my_project/.git/
 ```
 For repositories that are to be considered a point of authority on defining
 the truth in respect to release and collaboration, issue the following:
 ```bash
 user@host:~$ git init --bare
 Initialized empty Git repository in /home/user/our_project/
 ```
 ## Use cases:
 - Start version control in a new project directory.
 - Reinitialize a repository to fix missing .git metadata.

> Notes: The difference between `git init`, and `git init --bare` layes
> squarely on the file structure created.
> For `git init`, gives you:
> /home/user/my_project/
> └── .git
>     ├── branches
>     ├── config
>     ├── description
>     ├── HEAD
>     ├── hooks
>     │   ├── applypatch-msg.sample
>     │   ├── commit-msg.sample
>     │   ├── fsmonitor-watchman.sample
>     │   ├── post-update.sample
>     │   ├── pre-applypatch.sample
>     │   ├── pre-commit.sample
>     │   ├── pre-merge-commit.sample
>     │   ├── prepare-commit-msg.sample
>     │   ├── pre-push.sample
>     │   ├── pre-rebase.sample
>     │   ├── pre-receive.sample
>     │   ├── push-to-checkout.sample
>     │   └── update.sample
>     ├── info
>     │   └── exclude
>     ├── objects
>     │   ├── info
>     │   └── pack
>     └── refs
>         ├── heads
>         └── tags
>
> 11 directories, 17 files
>
> As, `git init --bare` gives you:
> /home/user/our_project
> ├── branches
> ├── config
> ├── description
> ├── HEAD
> ├── hooks
> │   ├── applypatch-msg.sample
> │   ├── commit-msg.sample
> │   ├── fsmonitor-watchman.sample
> │   ├── post-update.sample
> │   ├── pre-applypatch.sample
> │   ├── pre-commit.sample
> │   ├── pre-merge-commit.sample
> │   ├── prepare-commit-msg.sample
> │   ├── pre-push.sample
> │   ├── pre-rebase.sample
> │   ├── pre-receive.sample
> │   ├── push-to-checkout.sample
> │   └── update.sample
> ├── info
> │   └── exclude
> ├── objects
> │   ├── info
> │   └── pack
> └── refs
>     ├── heads
>     └── tags
>
> 10 directories, 17 files
