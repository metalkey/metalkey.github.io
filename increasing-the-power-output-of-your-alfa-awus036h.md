Increasing the Power Output of your Alfa AWUS036H
Warning: Check the laws in your region before adjusting the power output of your wifi adapter. Increasing the power above 20dBm can be a breach of regulations in some countries.

**OS:** Kali Linux
##Checking the Current Power Output
In the example below Tx-Power is set to the default value of 20dBm for the current locale.<br>
Information on how this value is determined is explained in-depth at Linux Wireless (<http://linuxwireless.org/en/developers/Regulatory/>)<br>
<code>
<div class="code">
root@kali:~$ <com>iwconfig</com><br>
<br>
wlan0 IEEE 802.11bg ESSID:off/any<br>
Mode:Managed Access Point: Not-Associated <com>Tx-Power=20 dBm</com><br>
Retry short limit:7 RTS thr:off Fragment thr:off<br>
Encryption key:off<br>
Power Management:off<br>

</div>
</code>
##Increasing the Output to 1-Watt (30dBm)
To increase the power output of the Alfa AWUS036H to 1-Watt (manufacturer specified maximum) you will need to change your locale to a region with different regulations (e.g. Belize – BZ) and set txpower manually.
<code>
<div class="code">
root@kali:~$ <com>ifconfig wlan0 down</com><br>
root@kali:~$ <com>iw reg set BZ</com><br>
root@kali:~$ <com>iwconfig wlan0 txpower 30</com><br>
root@kali:~$ <com>ifconfig wlan0 up</com><br>
root@kali:~$ <com>iwconfig</com><br>
<br>
wlan0 IEEE 802.11bg ESSID:off/any<br>
Mode:Managed Access Point: Not-Associated <com>Tx-Power=30 dBm</com><br>
Retry short limit:7 RTS thr:off Fragment thr:off<br>
Encryption key:off<br>
Power Management:off<br>

</div>
</code>
We have successfully set txpower to 30dBM (1-Watt).<br>
Higher values can also be set and detailed instructions are available at Null Byte (<http://null-byte.wonderhowto.com/how-to/set-your-wi-fi-cards-tx-power-higher-than-30-dbm-0149606/>).

Tags: wifi
