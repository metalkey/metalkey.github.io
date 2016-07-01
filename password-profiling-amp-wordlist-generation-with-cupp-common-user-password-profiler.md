Password Profiling & Wordlist Generation with CUPP (Common User Password Profiler)

**OS:** Debian 8<br>
<br>
CUPP was created by Muris Kurgas (aka j0rgan) from remote-exploit (<http://remote-exploit.org/>) and is an excellent tool for password profiling and wordlist optimization.
##Installation
To install, simply clone the git repo.
<code>
<div class="code">
<font color="silver">user@debian8:~$</font> <b>git clone https://github.com/Mebus/cupp.git</b><br>
<font color="silver">user@debian8:~$</font> <b>./cupp.py</b><br>
<br>
<b>-i</b> <font color="silver">Interactive questions for user password profiling</font><br>
<b>-w</b> <font color="silver">Use this option to improve existing dictionary, or WyD.pl output to make some pwnsauce</font><br>
<b>-l</b> <font color="silver">Download huge wordlists from repository</font><br>
<b>-a</b> <font color="silver">Parse default usernames and passwords directly from Alecto DB. Project Alecto uses purified databases of Phenoelit and CIRT which where merged and enhanced.</font><br>
</div>
</code>
##Password Profiling
In this example we will password profile the user "John Smith".<br>
We have some basic information on this user and will fill out the appropriate fields.<br>
<code>
<div class="code">
<font color="silver">user@debian8:~$</font> <b>./cupp.py -i</b><br>
<br>
<font color="silver">[+] Insert the informations about the victim to make a dictionary</font><br>
<font color="silver">[+] If you don't know all the info, just hit enter when asked! ;)</font><br>
<br>
<font color="silver">> First Name: </font><b>John</b><br>
<font color="silver">> Surname: </font><b>Smith</b><br>
<font color="silver">> Nickname: </font><b>John</b><br>
<font color="silver">> Birthdate (DDMMYYYY): </font><b>12011955</b><br>
<br>
<font color="silver">> Partners) name: </font><b>Mary</b><br>
<font color="silver">> Partners) nickname: </font><b>Mary</b><br>
<font color="silver">> Partners) birthdate (DDMMYYYY): </font><b>01031955</b><br>
<br>
<font color="silver">> Child's name: </font><b>Mark</b><br>
<font color="silver">> Child's nickname: </font><b>Mark</b><br>
<font color="silver">> Child's birthdate (DDMMYYYY): </font><b>01011982</b><br>
<br>
<font color="silver">> Pet's name: </font><b>Tim</b><br>
<font color="silver">> Company name: </font><b>Amazon</b><br>
<br>
<font color="silver">> Do you want to add some key words about the victim? Y/[N]: </font><b>y</b><br>
<font color="silver">> Please enter the words, separated by comma. [i.e. hacker,juice,black], spaces will be removed: </font><b>chelsea,football,beer,beatles</b><br>
<font color="silver">> Do you want to add special chars at the end of words? Y/[N]: </font><b>y</b><br>
<font color="silver">> Do you want to add some random numbers at the end of words? Y/[N]</font><b>y</b><br>
<font color="silver">> Leet mode? (i.e. leet = 1337) Y/[N]: </font><b>y</b><br>
<br>
<font color="silver">[+] Now making a dictionary...</font><br>
<font color="silver">[+] Sorting list and removing duplicates...</font><br>
<font color="silver">[+] Saving dictionary to john.txt, counting 40248 words.</font><br>
<font color="silver">[+] Now load your pistolero with john.txt and shoot! Good luck! </font><br>
</div>
</code>
Our 40,248 line wordlist has been generated and saved as "john.txt"
<code>
<div class="code">
<font color="silver">user@debian8:~$ </font><b>more john.txt</b><br>
<br>
<font color="silver">...</font><br>
<font color="silver">395503</font><br>
<font color="silver">39551955</font><br>
<font color="silver">39551955</font><br>
<font color="silver">395555</font><br>
<font color="silver">...</font><br>
<font color="silver">4m420n</font><br>
<font color="silver">4m420n!</font><br>
<font color="silver">4m420n!!</font><br>
<font color="silver">4m420n!!!</font><br>
<font color="silver">...</font><br>
<font color="silver">B33r1955355</font><br>
<font color="silver">B33r195555</font><br>
<font color="silver">B33r1955551</font><br>
<font color="silver">B33r1955552</font><br>
<font color="silver">...</font><br>
<font color="silver">Ch3l5342101</font><br>
<font color="silver">Ch3l5342112</font><br>
<font color="silver">Ch3l534212</font><br>
<font color="silver">Ch3l5342121</font><br>
<font color="silver">...</font><br>
<font color="silver">j0hnSm17h48</font><br>
<font color="silver">j0hnSm17h49</font><br>
<font color="silver">j0hnSm17h5</font><br>
<font color="silver">j0hnSm17h50</font><br>
<font color="silver">...</font><br>
</div>
</code>
This wordlist may prove useful when cracking hashes, capture files, etc…<br>
You can also download wordlists and improve wordlists using the -w, -l and -a options.<br>

Tags: password
