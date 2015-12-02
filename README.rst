rmate
=====

The ``rmate`` program enables editing files on a remote computer with
TextMate 2 via an SSH connection. This is a port of `the official Ruby
version`_ and was made for system that cannot (or just preferably do not) have
Ruby installed. This version (very intentionally) has no dependencies beyond
the Python standard library and has been tested with Python versions 2.4 - 3.5.

This port is probably compatible with Sublime Text, Atom, or other editors that
use the ``rmate`` protocol, but it is not officially tested.


Install
-------

Standalone
~~~~~~~~~~

``rmate`` is a single file script, so you can simply download it to a location
in your ``PATH``. For example, assuming ``/usr/local/bin`` is in the ``PATH``

::

    wget https://raw.githubusercontent.com/sclukey/rmate-python/master/bin/rmate
    chmod +x ./rmate
    mv ./rmate /usr/local/bin/rmate


PyPI
~~~~

You can also install ``rmate`` with ``pip``

::

    pip install rmate


SSH Connection Settings
~~~~~~~~~~~~~~~~~~~~~~~

For ``rmate`` to be able to connect back to TextMate, a port must be tunneled
through the ssh connection. By default, ``rmate`` uses port 52698, and the port
can be tunneled for an individual connection on the command line
::

    ssh -R 52698:localhost:52698 user@example.com

or for all connections by adding a rule to your ``~/.ssh/config``

::

    Host *
    RemoteForward 52698 localhost:52698

Usage
~~~~~

You can use ``rmate --help`` to see the usage

::

    usage: rmate [OPTION]... FILE...

          --host HOST  Connect to HOST. Use 'auto' to detect the host from
                       SSH. Defaults to localhost
      -p, --port PORT  Port number to use for connection. Defaults to 52698
      -w, --[no-]wait  Wait for file to be closed by TextMate
      -l, --line LINE  Place carat on line LINE after loading the file.
                       TextMate selection strings can be used
      -m, --name NAME  The display name shown in TextMate
      -t, --type TYPE  Treat file as having TYPE
      -f, --force      Open even if the file is not writable
      -v, --verbose    Verbose logging messages
      -h, --help       Show this help and exit
          --version    Show version and exit

    When FILE is -, read standard input.

More information can be found in `this blog post`_

.. _the official ruby version: https://github.com/textmate/rmate
.. _this blog post: http://blog.macromates.com/2011/mate-and-rmate/
