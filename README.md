# Linux Commands
This is simply a list of interesting, useful, or fun Linux commands.

## Utility
### General
* `cd`: Go to home
* `cd -`: Go to previous directory stored in `OLDPWD` env.
* `ALT + .`: Grabs the last argument of the last command. You can keep using this.
* `CTL + ALT + F#`: Changes TTY terminal you are viewing.
* `CTL + R`: Reverse Search (search list of previous commands).
* `ll`: sometimes systems alias *ll* to *ls -l*
* `lvs`: List logical volumes.
* `lsblk`: List block devices.
* `df`: Display disk usage.
  * `-H`: Human readable.
### Git
* `git remote update`: This will update all of the branches that we are currently set to track, unlike `git fetch` which will only update the information for the branch we are currently on. This does not merge the changes into our current files!
* `git push --mirror <URL>`: Push changes to the specified UR. This will also include any *refs* and things used by the *remote* branch to track changes. So we would use this if we are uploading our entire repository to another hosting provider. You should only use this once on the initial push!
* `git status`: Display the current state of the git repository. Are there untracked modifications, what has and has not been staged? This helps us track the state of the system!
* `git checkout`: Updates files to match the given tree or commit ID (index).
  * `-b`: This causes a new branch to be created.
* `git switch`: Allows us to switch the branch we are currently on.
* `git branch`: Allows us to list the current branch we are on with no arguments, or if arguments are provided it will create those branches.
* `git format-patch -1 --cover-letter -v1 --rfc`: 
  * Remember to edit hte file to add a subject and a blurb.
### SSH
* `ssh -L <listen-port>:<target:port> user@hostname`: Setup a local listener that will forward traffic over the ssh tunnel to the specified target through the remote machine you connected to.
* `ssh -R <listen-port>:<target:port> user@hostname`: Setup a remote listener that will forward traffic over the ssh tunnel to the specified target from the remote machine through the ssh tunnel to yours.
> [!NOTE]
> Generally we pair the ssh tunnels (forwarding) with a `-N` and `-f` to not request a shell and put it in the background.

## Fun
* `write`: Command used to write messages to the other terminal. Simply injects the messages onto the screen.
  * `writeall`: This will send to all users.
  * That is `wall`
* ls `/proc/PROCNUM/fd` lists the file descriptors used by the process.