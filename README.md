# Microbiology-675

# Intro 1/22/19
* CPU executes commands
* Memory/RAM is short term storage for programs being run (not permanent)
* Disk space is long term storage (permanent)
* "High speed" CPU is not really the limitation of computers
  * limitation is how fast information can be given to the CPU, determined by the frontside bus through which information from the  northbridge memory (from RAM) is channeled to the CPU.

## Language:
* We think of numbers to the base 10, computers use base 2.
* Base 2 means something is either on or off (1 or 0).

## Windows, Mac, Unix/Linux
* For Windows, the kernel is stacked with the operating system above it and the program is submitted above that. Kernel is where everything germinates/runs from. Doesn't allow users and programs to access the kernel directly (which was thought that it would be harder to hack/break those computers).
* For Unix/Linux, the kernel is accessed by programs directly. The operating system (O/S) is next to it, not stacked on top.
* Mac moved towards the way Unix/Linux does things.


# Introduction to Command Line 1/24/19
* Root access is access to the kernel
 * Do not need root access to install run/programs, just need administrative access
* Basic command line
 * Modify the behavior of `ls` and other commands with flags.
  * `-lap` : lists everything in directory, including hidden files.
  * `-l` : long list format
  * `-a` : shows hidden files
* My home Windows partition when opening Ubuntu can be accessed by:
 1. `cd ..` and `cd ..` again
 2. `cd mnt` then `cd c` then `cd Users` then `cd Shannon`
 3. Then I can access all of my Windows files.
  
