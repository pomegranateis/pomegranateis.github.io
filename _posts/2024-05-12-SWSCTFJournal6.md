---
Title: SWS101 Journal
categories: [SWS101, CTFjournal]
tags: [SWS101]
---

# Topic: Simple CTF

## Task 1: Simple CTF

1. How many services are running under port 1000?

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-48-01.png>)

Answer: 2

2. What is running on the higher port?

Using **-A** will get more information.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-50-16.png>)

There is FTP with anonymous login, a robot.txt file and SSH access.

Answer: SSH

3. What’s the CVE you’re using against the application?

Using gobuster to find out files/directories.

![alt text](<../assetsassets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-53-23.png>)

There is a /simple directory.

![alt text](<../aassets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-54-27.png>)

More information can be found here.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-56-05.png>)

Answer: CVE-2019–9053

4. To what kind of vulnerability is the application vulnerable?

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-57-29.png>)

The application is vulnerable to SQL injection.

Answer: SQLi

5. What’s the password?

Download the script using ***wget***

Then I can run python by using ***python2 exploit.y -u <url>***

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 04-06-28.png>)

Since I want to find the password I need to use the -c flag togetheer with the -w flag.

***python2 exploit.py -u <url> -c -w /usr/share/wordlists/rockyou.txt***

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 04-08-07.png>)

Answer: secret

6. Where can you login with the details obtained?

Since we already have used ssh, let me try logging in.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 04-09-47.png>)

Answer: SSH

7. What’s the user flag?

Directly run **ls** followed by **cat user.txt**.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 04-11-21.png>)

Answer: G00d j0b, keep up!

8. Is there any other user in the home directory? What’s its name?

Since I am in mitch home dir, I need to go one dire up and list the folders.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 04-13-57.png>)

Answer: Sunbath

9. What can you leverage to spawn a privileged shell?

Check the allowed commands for the user.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 04-14-53.png>)

I got access to the vim shell.

Answer: Vim

10. What’s the root flag?

Use vim to gain root shell. 

***sudo vim -c ‘:!/bin/sh’***

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 04-17-27.png>)

Answer: W3ll d0n3. You made it!
