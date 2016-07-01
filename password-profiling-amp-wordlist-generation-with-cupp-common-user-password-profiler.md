Password Profiling & Wordlist Generation with CUPP (Common User Password Profiler)

**OS:** Debian 8<br>
<br>
CUPP was created by Muris Kurgas (aka j0rgan) from remote-exploit (<http://remote-exploit.org/>) and is an excellent tool for password profiling and wordlist optimization.
##Installation
To install, simply clone the git repo.
<code>
<div class="code">
user@debian8:~$ <com>git clone https://github.com/Mebus/cupp.git</com><br>
user@debian8:~$ <com>./cupp.py</com><br>
<br>
<com>-i</com> Interactive questions for user password profiling<br>
<com>-w</com> Use this option to improve existing dictionary, or WyD.pl output to make some pwnsauce<br>
<com>-l</com> Download huge wordlists from repository<br>
<com>-a</com> Parse default usernames and passwords directly from Alecto DB. Project Alecto uses purified databases of Phenoelit and CIRT which where merged and enhanced.<br>
</div>
</code>
##Password Profiling
In this example we will password profile the user "John Smith".<br>
We have some basic information on this user and will fill out the appropriate fields.<br>
<code>
<div class="code">
user@debian8:~$ <com>./cupp.py -i</com><br>
<br>
[+] Insert the informations about the victim to make a dictionary<br>
[+] If you don't know all the info, just hit enter when asked! ;)<br>
<br>
> First Name: <com>John</com><br>
> Surname: <com>Smith</com><br>
> Nickname: <com>John</com><br>
> Birthdate (DDMMYYYY): <com>12011955</com><br>
<br>
> Partners) name: <com>Mary</com><br>
> Partners) nickname: <com>Mary</com><br>
> Partners) birthdate (DDMMYYYY): <com>01031955</com><br>
<br>
> Child's name: <com>Mark</com><br>
> Child's nickname: <com>Mark</com><br>
> Child's birthdate (DDMMYYYY): <com>01011982</com><br>
<br>
> Pet's name: <com>Tim</com><br>
> Company name: <com>Amazon</com><br>
<br>
> Do you want to add some key words about the victim? Y/[N]: <com>y</com><br>
> Please enter the words, separated by comma. [i.e. hacker,juice,black], spaces will be removed: <com>chelsea,football,beer,beatles</com><br>
> Do you want to add special chars at the end of words? Y/[N]: <com>y</com><br>
> Do you want to add some random numbers at the end of words? Y/[N]<com>y</com><br>
> Leet mode? (i.e. leet = 1337) Y/[N]: <com>y</com><br>
<br>
[+] Now making a dictionary...<br>
[+] Sorting list and removing duplicates...<br>
[+] Saving dictionary to john.txt, counting 40248 words.<br>
[+] Now load your pistolero with john.txt and shoot! Good luck! <br>
</div>
</code>
Our 40,248 line wordlist has been generated and saved as "john.txt"
<code>
<div class="code">
user@debian8:~$ <com>more john.txt</com><br>
<br>
...<br>
395503<br>
39551955<br>
39551955<br>
395555<br>
...<br>
4m420n<br>
4m420n!<br>
4m420n!!<br>
4m420n!!!<br>
...<br>
B33r1955355<br>
B33r195555<br>
B33r1955551<br>
B33r1955552<br>
...<br>
Ch3l5342101<br>
Ch3l5342112<br>
Ch3l534212<br>
Ch3l5342121<br>
...<br>
j0hnSm17h48<br>
j0hnSm17h49<br>
j0hnSm17h5<br>
j0hnSm17h50<br>
...<br>
</div>
</code>
This wordlist may prove useful when cracking hashes, capture files, etc…<br>
You can also download wordlists and improve wordlists using the -w, -l and -a options.<br>

Tags: password
