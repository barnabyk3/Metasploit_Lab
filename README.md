# Metasploit_Lab
The other night in the Evolve Cybersecurity Boot Camp, our cohort was guided through a super simple Metasploit
exploitation.  I wrote this writeup for others to understand it, also using Github for the first time this way.

![image](https://user-images.githubusercontent.com/83624183/117094337-cb854680-ad20-11eb-88ea-a0049748dffa.png)


This first screenshot shows me using nmap. First I scan the entire network of an IP with a general scan. 
Then, once I've identified the IP with the vulnerabilities I want to target, I'm re-scanning it using the
-sV switch, which will hopefully show me versions of operating systems and programs running.

![image](https://user-images.githubusercontent.com/83624183/116955136-ed15fd80-ac4e-11eb-8b29-c9bb34135356.png)

I open a new tab in my terminal and type in msfconsole to start the Metasploitable Framework. This is essentially
a program that aggregates all kinds of tools and programs that can be used to attack a machine. There are many
Exploits in it, which are programs that take advantage of very specific bugs or weaknesses in operating systems
or other software that hackers somewhere discovered. 

![image](https://user-images.githubusercontent.com/83624183/116955333-7decd900-ac4f-11eb-8d45-7cdf2eca66da.png)

![image](https://user-images.githubusercontent.com/83624183/116955380-a07ef200-ac4f-11eb-9bfc-73ba55cbd596.png)

These next two screenshots illustrate the process of my searching for an exploit. What I have not shown is that
my second nmap scan found a program running on one of the ports called, ProFTPd 1.3.3 
In the first image you can see cut off at the top, that I typed in searchsploit proftpd 1.3.3; and then at the
right side below the utility came up with a bunch of exploits. These are all stored in Kali Linux already, and
refered to by numbers, for instance 16921.rb at the very bottom right. Kali Linux is so awesome!

![image](https://user-images.githubusercontent.com/83624183/117094371-e061da00-ad20-11eb-8216-f96a454bdc7f.png)


Metasploit contains modules, which are essentially prepackaged exploits, and are designed to make using
the exploit super easy. In this screenshot the name and file path are in red, indicating that is the 
module I am inside. When I typed 'show options', a little chart popped up showing what information I needed
to enter to make it work. Next to RPORT there is already a port number that works, number 21 so I won't change
that. There is a blank next to RHOSTS, however, as well as 'yes' written under 'Required' which indicates a 
value does need to be there. RHOSTS are the host IP's I want to attack. And so, I type 'set RHOSTS <Target IP>

![image](https://user-images.githubusercontent.com/83624183/117094391-eeaff600-ad20-11eb-9e63-1f74fcbf7cc1.png)


Once I have filled out the information for the IP addresses and ports I want the exploit to attack, I can shoot 
it downrange at the machine I am attacking simply by typing 'exploit' at the module's prompt, as you see here.
The program lists the steps as it achieves them, including in the last line giving the IP address and Port number
that the command shell is linking from and to in order to give me the remote shell. A remote shell is essentially
like sitting in front of the computer I attacked, and getting to type in to it what I want as if I were there.
As you can see, I typed the command 'whoami' to which the machine responded, 'root'. This is the best possibe
scenario, where I can now do anything I want with godlike administrator powers.

![image](https://user-images.githubusercontent.com/83624183/117094106-1c486f80-ad20-11eb-8016-e6ce50a4cbaa.png)

This final screenshot shows a process where I uploaded an extra little program
which creates a much more stable shell (terminal, like where you are sitting in
front of the computer) that is much less likely to accidentally crash or stop 
working. This is usually important to do before an attacker starts to really do
work on the machine they attack. 
First I pressed control-Z, and responded yes to 'background' the session. Next
I typed in 'sessions' to list that one session. This allows me to keep that
exploit running, while I continue to work in my own computer. 
Then I typed in 'sessions -u 1' which essentially told the Meterpreter 
program to Upgrade the session as I just described. It's a totally automated
process, that allows me not to have to dig around searching for the computer
codes online which will achieve this, and not have to send them to the victim
machine using potentially complicated commands. It's being able to do all those
things manually that really make a person a good hacker, but Metasploitable and 
Meterpreter do these things quickly and automatically for you.
Finally at the bottom I listed the sessions again, and typed 'sessions -i 2' which
allows me to interact with the second session, which is where that Meterpreter
(more stable shell) is running. That is why the last line at the bottom is the
Meterpreter command prompt.

Viola! Most excellent hacking dude! Party on Wayne






