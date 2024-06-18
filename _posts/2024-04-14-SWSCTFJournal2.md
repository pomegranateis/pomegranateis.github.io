---
Title: SWS101 Journal
categories: [SWS101, CTFjournal]
tags: [SWS101]>
---

# TryHackMe Basic Pentesting

### Task 1 Web App Testing and Privilege Escalation

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 18-38-19.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-10-52.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-41-15.png>)

*The second task is about finding hidden paths in the web server.*

In order to do that you should use one of the directory enumerator programs. In this case i’m using gobuster with dirbuster wordlist.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-19-34.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-23-48.png>)

If you go back and look at the nmap scan result, you will see that the samba service is running. So I’ll use enum4linux program to find users.

*Enum4linux is a tool for enumerating information from Windows and Samba systems.*

After running **enum4linux** program, i have found 2 accounts.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-26-23.png>)

First username is **jan**.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-43-31.png>)

After founding the users you are prompted to find the password of the user(Jan in this case)

If you go back and look at the nmap scan result, you will see that the SSH service is running. So I’ll use **hydra** to brute forcing to SSH service.

*Hydra is a parallelized login cracker which supports numerous protocols to attack.*

I hope to find jan’s password this way. I’ll use **rockyou.txt** as a wordlist.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-47-57.png>)

After running hydra I’ve found password of jan. The password is **armando**.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-50-38.png>)

The other question in this task is “What service do you use to access the server?”

In this case we used ssh service so the answer will be **SSH**.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-52-37.png>)

The fourth task is about the privilege escalation.

We found jan’s password before. Let’s log in with password that we found.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-53-44.png>)

To enumerate weaknesses and privilege escalation opportunities I’ll use **linPEAS.**

First I’ll download the linPEAS script to my machine.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 15-54-57.png>)

After downloading the linPEAS script, i should copy the script to the target machine. In order to do that I’ll use SCP.

After copying the linPEAS script, I’ll make it executable and run it.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-13 16-00-05.png>)

While script running it found an id_rsa(SSH Private Key) under the kay’s home directory.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-14 17-40-54.png>)

As you can see the private key is password protected. Imust crack this password. In order to do that I'll use *JohnTheRipper* to brute force the password.

After copying the private key to my computer I'll run it with the rouckyou.txt wordlist.

Before I start I need to make the id_rsa file compatible with JohnTheRipper. In order to do that I'll use **ssh2john.py**

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-14 17-45-57.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-14 17-46-50.png>)

Okay! I've found the password of the private key.

To connect to the target machine via SSH with kay;s ssh private key.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-14 17-48-44.png>)

Now I'm in.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-14 17-49-39.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-14 17-50-19.png>)


![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-14 17-52-09.png>)