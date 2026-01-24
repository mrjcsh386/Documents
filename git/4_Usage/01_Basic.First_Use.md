# Actions to take before doing work with git tooling.
 On first use, Git requires an initial configuration to set your identity.
 These steps are a direct result of sensitivity to political structures.

 ```bash
 user@host:~$ git config --global user.name "Your Name"
 user@host:~$ git config --global user.email "your.email@example.com"
 ```
 Example configuration files are located in 04_Configuration/etc/gitconfig
 and home/user/.gitconfig.

   Default branch of 'master' is created without configuring the following.
 Doing so is considered good form. take this as you will.
 ```bash
 user@host:~$ git config --global init.defaultBranch main
 ```

   The Following are niceties that I add for myself. Mildly opinionated,
 of course!
 ```bash
 # Enable pretty output
 user@host:~$ git config --global color.ui auto

 # Enabling caching of credentials for 15 minutes (passwords, keys, etc)
 user@host:~$ git config \
  --global credential.helper 'cache --timeout=900'

 # Set your preferred text editor for commit messages and handling
 # conflicts.
 user@host:~$ git config --global core.editor 'vi'
 # Replace editor for your choice

 # Configure for a global '.gitignore' kept in your home directory.
 git config --global core.excludesfile '~/.gitignore_global'
 ```

   Example configuration files are located in 04_Configuration/home/user\
 .gitignore[_global]*
 ```bash
 # Ensure consistent handling of line endings across different
 # operating systems.

 # For Linux, BSD, Unix, or Apple products, enter:
 user@host:~$ git config --global core.autocrlf input

 # For Microsoft products, enter:
 bash$ git config --global core.autocrlf true
 ```
 ```bash
 # A more widely used alias for 'log':
 user@host:~$ git config --global alias.lg "log --oneline --graph \
  --decorate --all"
 ```

> Notes: For a first time user of `git`, you'll start to notice `--global`,
> `--local`, and `--system`. `--system` affects /etc/gitconfig, `--global`
> affects ~/.git/config, as `--local` affects te repository you are currently
> working on. So, if you're using a different identity for a particular repo,
> use `--local` for *that* repository.
