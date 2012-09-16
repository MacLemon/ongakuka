# Ongakuka

A simple ssh tunnel setup script to ssh tunnel an iTunes connection to a remote mt-daapd server.


## License
Simplified BSD license (aka Two-clause BSD)
See LICENSE


## Prerequisites
A working `mt-daapd` server running on port 13689 and `ssh` access to the network that server resides on. An installation via MacPorts[2] is just fine.
Working SSH account with non-interactive key authentication. There are tons of tutorials available on the interwebs on how to set this up correctly.
Ability to tunnel ports with SSH. You do not need to be able to spawn a shell.



## Setup
Setup a host configuration in your `~/.ssh/config` like this
Replace the hostname and identity key filename, etc. accordingly.

Host nickname must be Ongakuka (capital O).

    host Ongakuka
        hostname ongakuka.example.com
        Compression yes
        IdentityFile ~/.ssh/id_rsa_ongakuka

Other recommended options
        TCPKeepAlive no
        ServerAliveInterval 60
        ServerAliveCountMax 10
        VisualHostKey no

If needed also add these ssh opions or any others you need.
        User ongakuka
        Port 10022


Put ongakuka or an alias to it somewhere in your `$PATH`.

To establish your tunnel simply run ongakuka from a Shell.
Once the tunnel has been established you should see a shared Music source in iTunes named "Ongakuka".
Use it like any other shared iTunes library. Expect your initial loading time to be longer than on the LAN.
Enjoy your music.
Once you're done, press any key to shut the tunnel down.

If we cannot find a binary to Bonjour announce the Tunnel we exit 127.

## Caveat
You can not use this to connect to a shared iTunes instance. iTunes prevents routing of daap packets by setting their TTL to 1.


## Links
[0]:https://twitter.com/MacLemon "@MacLemon" Author of ongakuka
[1]:http://sourceforge.net/projects/mt-daapd/ "mt-daapd"
[2]:http://macports.org/ "MacPorts"
