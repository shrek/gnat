gnat is a wrapper around the libjingle library. It allows
client-server applications such as VNC etc to work over libjingle
transport. The clients can (detect the presence of and) address the servers
by their Jabber IDs
allowing the servers to be on private IPs. This expands the addressable
internet.

It was motivated by the problem of accessing a home
computer when traveling. This utility can be used along with
[ultra-vnc](http://www.uvnc.com)
for this,  and it works great !


### How to run VNC over Libjingle ###

On Computer 1 (server)
```
Run VNC server and configure the server to accept local connections

Then run the gnat application on the command-line
       gnat.exe
          JID: xyz@gmail.com
          Password:
          Available commands:

              roster       - Prints the online friends from your roster.
              pipe jid local-port remote-port [udp|tcp] -  Initiate a pipe.
              show  - shows state of pipes
              quit     -    Quits the application.
          
```

On Computer 2 (client)
```
First run the gnat application on the command-line
        gnat.exe
          JID: abcd@gmail.com
          Password:
          Available commands:

              roster       - Prints the online friends from your roster.
              pipe jid local-port remote-port [udp|tcp] -  Initiate a pipe.
              show  - shows state of pipes
              quit     -    Quits the application.

          Logging in.
          Logged in as abcd@gmail.com/pcpEBEB27A6

        roster
          Roster contains 1 callable
          xyz@gmail.com/pcp9FB543CC - online

Setup a pipe to the target -- Note that target address is not an IP address but
a JID (xyz@gmail.com/pcp9FB543CC), 9999 is the local port, and 5900 is the
VNC server port on the target 

        pipe xyz@gmail.com/pcp9FB543CC 9999 5900 tcp 
          src server started, listening at 127.0.0.1:9999

At this point run the Vnc client application, and connect to address: 127.0.0.1:9999

          accepted connection from 127.0.0.1:58201
          initiating tunnel to user xyz@gmail.com/pcp9FB543CC
          Tunnel connected

```

### Other applications that work with gnat/libjingle ###

  * [Unison](http://www.cis.upenn.edu/~bcpierce/unison/) for file sync between computers
  * [VLC](http://www.videolan.org/vlc/) media player

### Related ###

P. Francis. "[Is the Internet Going NUTSS?](http://nutss.gforge.cis.cornell.edu/pub/ieee-nutss.pdf)," in IEEE Internet Computing, vol. 7, no. 6, pp. 94--96, 2003.

[vncviaxmpp](http://code.google.com/p/vncviaxmpp/)