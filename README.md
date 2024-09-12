# Linux Commands
This is simply a list of interesting, useful, or fun Linux commands.

## Utility
* `cd`: Go to home
* `cd -`: Go to previous directory stored in `OLDPWD` env.
* `ALT + .`: Grabs the last argument of the last command. You can keep using this.
* `CTL + ALT + F#`: Changes TTY terminal you are viewing.
* `CTL + R`: Reverse Search (search list of previous commands).

## Fun
* `write`: Command used to write messages to the other terminal. Simply injects the messages onto the screen.
  * `writeall`: This will send to all users.
  * That is `wall`
* ls `/proc/PROCNUM/fd` lists the file descriptors used by the process.