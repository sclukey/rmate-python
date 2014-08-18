# rmate

The `rmate` program enables editing files on a remote computer with TextMate 2 via an SSH connection. This Python implementation works with both Python 2 and Python 3.

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

	usage: rmate [--host HOST] [-p PORT] [-w] [-l NUMBER [NUMBER ...]]
	             [-m NAME [NAME ...]] [-t TYPE [TYPE ...]] [-f] [-v] [-h]
	             [--version]
	             [file [file ...]]
	
	Activate TextMate from an SSH session
	
	positional arguments:
	  file                  File to open
	
	optional arguments:
	  --host HOST           Connect to host. Use 'auto' to detect the host from
	                        SSH. Defaults to localhost
	  -p PORT, --port PORT  Port number to use for connection. Defaults to 52698
	  -w, --wait            Wait for file to be closed by TextMate.
	  -l NUMBER [NUMBER ...], --line NUMBER [NUMBER ...]
	                        Place caret on line [NUMBER] after loading file.
	  -m NAME [NAME ...], --name NAME [NAME ...]
	                        The display name shown in TextMate
	  -t TYPE [TYPE ...], --type TYPE [TYPE ...]
	                        Treat file as having [TYPE]
	  -f, --force           Open even if the file is not writable.
	  -v, --verbose         Verbose logging messages.
	  -h, --help            Show this message.
	  --version             Show version.
