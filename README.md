# rmate

The `rmate` program enables editing files on a remote computer with TextMate 2 via an SSH connection. This Python implementation has been tested with versions 2.4-3.4.

## Setting up `rmate`

### Getting the program

To use `rmate`, you need to copy the script to the remote machine and make it executable

	wget https://raw.github.com/sclukey/rmate/master/rmate
	chmod +x ./rmate

The make the script accessible from anywhere, simply move it to a location within your `PATH` environment variable

	mv ./rmate /usr/local/bin/rmate

### Setting up the connection

For the program to be able to connect back to TextMate a port must be tunneled in the ssh connection. This can be done by just adding an option to tunnel the port in the SSH connection command

	ssh -R 52698:localhost:52698 user@example.com

or by adding a rule to your `~/.ssh/config`

	Host *
	RemoteForward 52698 localhost:52698

### Usage

You can use `rmate --help` to see the usage

	usage: rmate [OPTION]... FILE...
	
	      --host HOST  Connect to HOST. Use 'auto' to detect the host from
	                   SSH. Defaults to localhost
	  -p, --port PORT  Port number to use for connection. Defaults to 52698
	  -w, --[no-]wait  Wait for file to be closed by TextMate
	  -l, --line LINE  Place carat on line LINE after loading the file.
	                   TextMate selection strings can be used
	  -m, --name NAME  The display name shown in TextMate
	  -t, --type TYPE  Treat file as having TYPE
	  -f, --force      Open even if the file is not wratable
	  -v, --verbose    Verbose logging messages
	  -h, --help       Show this help and exit
	      --version    Show version and exit
	
	When FILE is -, read standard input.
