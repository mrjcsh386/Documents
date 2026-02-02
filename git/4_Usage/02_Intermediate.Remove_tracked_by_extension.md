# Remove tracked files by extension

## Summary:
At some point, let's say you have tracked a .swappity_mc.swp file and wish to
remove it from Gits tracking engine. You may have even added it to .gitignore,
and find it's still being tracked

## Example:
If you still see them after adding `*.swp`, the only remaining culprit is
"already tracked". The one-liner I reach for is:
 ```bash
 user@host:~$ git rm --cached -r -- \
   '*.swp' '*.swo' '*.sw?' 2>/dev/null || true
 user@host:~$ git status
 ```

## Use cases:
- Remove previously tracked files
