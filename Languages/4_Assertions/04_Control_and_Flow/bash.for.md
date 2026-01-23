## Bash: for control structure
---
   Syntactically, bash has **three** `for` forms.
   Semantically, `for` expresses **at least two funcamentally different models**:
 - expansion-driven iteration
 - state-driven iteration

 Algorithmically, it can play **many roles**, but they all reduce to one idea:

 Bind a name to a sequence, in order, and let time pass.

 That's why `for` is so powerful in shell. It doesn't try to be clever. It gives
 you structure, and then it gets out of the way.

 ```bash
 for variable in values
 do
   statements
 done
 ```

 Now, here is the interesting bits:

---

 ## List form (`for name in words`)
 ```bash
 for x in a b c; do
   echo "$x"
 done
 ```
   This is the primordial form. `x` is bound to each word, from left to right.
 What this *means* depends entirely on where the words come from.

 ### Static words
 ```bash
 for x in one two three; do
   echo "$x"
 done
 ```
 ### Brace expansion
 ```bash
 for x in {1..5}; do
   echo "$x"
 done
 ```
 ### Glob expansion
 ```bash
 for x in *; do
   echo "$x"
 done
 ```
 ### Command substitution
 ```bash
 for x in $( printf "a b c" ); do
   echo "$x"
 done
 ```
