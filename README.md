# What's wrong? #

A simple bash script to do some basic checks on the system, and 
report any problems found.  The basic concept is that this script
should be run as a first step when debugging any issue.
Nothing in the script requires root privileges to run.

Please note that there are some situations where this script may cause
a system with problems to hang, for example if there are unavailable
mounted volumes.

You can run on any system with internet access directly, even if the
disks are remounted read-only:

`curl https://raw.github.com/BashtonLtd/whatswrong/master/whatswrong |
bash`

Alternatively, as long as you have SSH access to the remote system you
can download via your local machine, and then send and execute over SSH 
as follows:

`curl https://raw.github.com/BashtonLtd/whatswrong/master/whatswrong |
ssh $remote_server bash`

You could add a commandline shortcut to this by appending the following
to your `.bashrc`:

`ww() { curl https://raw.github.com/BashtonLtd/whatswrong/master/whatswrong |
ssh $1 bash; }`

You can then run the script on any machine you have SSH access to with
`ww $remote_server`

You may need to add -k to curl, however, beware that this increases
the potential for a man-in-the-middle attack.  As the script is not run
as root, this is less serious than it might otherwise be, but should
still be considered.
