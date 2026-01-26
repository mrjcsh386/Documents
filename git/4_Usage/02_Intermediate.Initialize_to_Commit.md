 ## Summary:
   Demonstrates a simple workflow of initializing a repository and
 adding files.

 ## Example:
 ```bash
 user@host:~$ git init my_project
 user@host:~$ cd my_project
 user@host:~/my_project$ echo "Hello" > file.txt
 user@host:~/my_project$ git add file.txt
 user@host:~/my_project$ git commit -m "Initial commit"
 ```
 ## Explanation:
   This sequence shows starting a repository, creating a file, staging it,
 and committing changes. It is an intermediate use of Git workflow. This
 would be in the basic, if it wasn't for the idea that you are now building
 repos instead of consuming them.
