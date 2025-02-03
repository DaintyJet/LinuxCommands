# Linux Commands
This is simply a list of interesting, useful, or fun Linux commands.

## Utility

### General
* `cd`: Go to home
* `cd -`: Go to previous directory stored in `OLDPWD` env.
* `ALT + .`: Grabs the last argument of the last command. You can keep using this.
* `CTL + ALT + F#`: Changes TTY terminal you are viewing.
* `ll`: sometimes systems alias *ll* to *ls -l*
* `lvs`: List logical volumes.
* `lsblk`: List block devices.
* `df`: Display disk usage.
  * `-H`: Human readable.
* `CTL+Z`: Puts a process in the background.
* `fg` puts the most recent job into the foreground.
* `jobs`: lists suspended jobs.
* `fg #`: brings that process to the foreground.
* `tac`: Prints out the text but backwards.
* `bat`: Cat but syntax highlighting.
* `dd`: Used to copy data from one device to another (blocks). We can use this to format the device too.
  * `if=<filename/device>`: Input
  * `of=<filename/device>`: Output
* `sudo -i`: Run multiple sudo commands one after another (looks like `sudo su`).
* `stat`: Provide detailed file information. Like the *inode* associated with the file, when it was last modified, created etc.
* `free`: Display basic information on free space on the system. Includes RAM and SWAP space for the system.
* `vmstat`: Display basic information on the virtual memory. Includes additional flags for mor detailed information like `--slabs`. This focuses more on *processes*.
* `dumpe2fs`: Print superblock and other file system information.
* `mount`: Display mounted filesystems or mount new devices.

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
* `git send-email`: Sends email based on the git configurations of the user.
  * (Optional) `--smtp-debug=1`: Displays debugging information.
  * `--to=setup@COURSE_DOMAIN`: Location to send.
  * `v1*.patch`: Files to send (If you create different versions change this!)
* `git grep`: Grep search within the bounds of the git repository ignoring git files and those ignored by `.gitignore`
  * `-n`: Tells us the line number.
### GDB
* `r`: Run
* `bt`: Backtrace
* `l`: Show current command if compiled with `-g`
* `disass`: disassemble instructions
### GCC
* `gcc`: GNU C Compiler
  * `-o`: Output file name. Traditionally will be `a.out` due to being *assembler output*.
  * `-ffreestanding`: No main function.
  * `-nostdlib`: Do not link to c-standard library.

### Kernel Modules
* `lsmod`: list the modules or information on a specified module.
* `rmmod`: Remove a module from the kernel (aggressive).
* `insmode`: Add a module to the kernel. Does not automatically load dependencies.
* `modprobe`: Add or remove a module from the kernel, resolve dependencies
### Assemblers/Objects
* `as`: Assembler used by gcc most of the time.
* `gas`: GNU assembler
* `nm`: List symbols from a specified object file.
* `readelf`: Parse the else file
* `objdump`: Dump the contents of an executable or object file.

### FTRACE
> [!IMPORTANT]
> This will take all your memory and ram if you leave it on.

* `/sys/kernel/tracing/*`: Directory containing files to control, and configure the *ftrace* utilities.
* `/sys/kernel/tracing/set_ftrace_pid`: Filter based on the PID of a process
* `/sys/kernel/tracing/tracing_on`: Put `0` in to stop tracing and `1` to start tracing.
* `/sys/kernel/tracing/trace`: Contains results of the trace.
> [!NOTE]
> You can use `echo` to modify the contents of the files, you can also use `dd` to copy the `trace` file to a place to analyze.
### SSH
* `ssh -L <listen-port>:<target:port> user@hostname`: Setup a local listener that will forward traffic over the ssh tunnel to the specified target through the remote machine you connected to.
* `ssh -R <listen-port>:<target:port> user@hostname`: Setup a remote listener that will forward traffic over the ssh tunnel to the specified target from the remote machine through the ssh tunnel to yours.
> [!NOTE]
> Generally we pair the ssh tunnels (forwarding) with a `-N` and `-f` to not request a shell and put it in the background.
### Making
* `make -j $(nproc)`: The *-j* flag allows us to use multiple threads in-parallel to build the project. The `nproc` command returns the number of CPU cores on your systems.
* `patch`: Patch command used to apply the `.patch` files onto the current directory. As we are sending `.patch` files to one another this is how we will be testing them (really wrapped around `git am`).
* `diff`: Program that displays the differences between two files. This is what makes up the majority of a `.patch` file.
### Tar
* `tar -tf`: allows us to view the files within a tar file without extracting them.
  * Add a `-v` for more file information, similar to the output we would see from `ls -l`
### Logs
* `dmsg`: View kernel code.
  * `-h`: Puts the output in human readable form.
### Mutt
* `/`: Like *less* this allows us to search for something (the name of our targets!).
## Packages Fedora
* `dnf -C rq --provides <PATH TO BIN>`: Query what package provides this thing
## Fun
* `write`: Command used to write messages to the other terminal. Simply injects the messages onto the screen.
  * `writeall`: This will send to all users.
  * That is `wall`
* ls `/proc/PROCNUM/fd` lists the file descriptors used by the process.
* `time`: This will time how long a command takes (user and system time).
