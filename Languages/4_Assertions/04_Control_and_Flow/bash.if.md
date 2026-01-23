### Bash: if control structure
---
   In bash, an `if` is really just: "did the last command exit with status 0?"
 Let's wander through some creative patterns, treating `if` less like a boring
 conditional and more like a Boolean algebra with side effects.

   At the heart of it, the following represents the core of it's logical flow:

 ```bash
 if <condition>
 then
   statements
 else
   statements
 fi
 ```

 So, in other words:
 
 ```bash
 if command; then
   echo "Exit code for command is: 0(true)"
 else
   echo "Exit code for command is: 1(false)"
 fi
 ```

 > Note: Assuming standard linux libraries are in effect, and exit codes are
 >       standarized in some way. 0, denotes pass or successful code completion.
 >       1, denotes fail or unsuccessful code completion. Everything between 2
 >       through 255 will indicate some sort of failure specifically.

   Here, you'll find some creative use of `if` and expressing it through Boolean
 algebraic expressions.
---
 ### NOT operation:
 ```bash
 # NOT logic gate
 if ! command; then
   echo "Exit code for command is: 1(false)"
 fi
 ```
 This demonstrates a clean logical inversion by including `!` within the
 conditional part of the `if` expression. 
---
 ### AND operation:
   With that, we take a look at AND:
 ```bash
 # AND logic gate
 if [ -f file.txt ] && [ -s file.txt ]; then
   echo "File exists AND is not empty"
 fi
 ```
 Here `&&` is literally Boolean AND. Both tests must return success. The same
 idea can be applied more abstractly, as:
 ```bash
 # More AND logic
 if grep -q "ERROR" logfile && systemctl is-active --quiet nginx; then
   echo "Error found AND nginx is running"
 fi
 ```
---
### OR operation:
   OR logic is the sibling that says "any one of you is good enough."
 ```bash
 # OR logic gate
 if [ "$USER" = "root" ] || [ "$EUID" -eq 0 ]; then
   echo "Running with elevated privileges"
 fi
 ```
> Note: The first comparisson you make takes precedence, consider your 
> priorities
---
 ### XOR operations
 XOR means, "exactly one is true.":
 ```bash
 if { condition_a && ! condition_b; } || { ! condition_a && condition_b; }; then
   echo "Exactly one condition is true"
 fi
 ```
 Another clever XOR trick uses exit codes directly:
 ```bash
 condition_a
 a=$?

 condition_b
 b=$?

 if [ $(( a + b )) -eq 1 ]; then
   echo "XOR satisfied"
 fi
 ```
 Here you're literally adding truth values. Zero is true, non-zero is false,
 so this one is more "conceptual" than idiomatic, but it makes the logic visual.

 ---
 ### NAND: Not (A and B)
 ```bash
 if ! ( condition_a && condition_b ); then
   echo "NAND triggered"
 fi
 ```
 ---
 ### NOR: Not (A or B)
 ```bash
 if ! ( condition_a || condition_b ); then
   echo "NOR triggered"
 fi
 ```
 Once you start thinking this way, bash scripts become more like logic circuits
 that happen to launch processes instead of lighting LEDs.

 Finally, a pattern I especially enjoy: decision tables disguised as logic.
 ```bash
 if [[ $mode == "prod" && $debug != "true" ]]; then
   log_level="error"
 elif [[ $mode == "prod" && $debug == "true" ]]; then
   log_level="warn"
 else
   log_level="debug"
 fi
 ```

---
 ### `elif` the middle child of shell control flow
   Not as blunt as `else`, not as decisive as a fresh `if`, and quietly doing
 the hard work of *ordering reality*. Think of it as a **chain of probes**,
 each one only tried if all previous ones failed.

   In bash, `elif` is not "else + if" glued together conceptually. It is more
 like a **series of probes**, evaluated top-down, first success wins, no
 backtracking.

 Here's the core shape, stripped of ceremony:
 ```bash
 if attempt_a; then
   act_a
 elif attempt_b; then
   act_b
 elif attempt_c; then
   act_c
 else
   act_default
 fi
 ```
 Read it literally:

 "Try A
    if that worked, stop.
  Otherwise try B.
    if that worked, stop.
  Otherwise try C.
    if that worked, stop
  If nothing worked so far.
    concede." 
 
