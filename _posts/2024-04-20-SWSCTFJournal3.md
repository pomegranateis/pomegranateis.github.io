---
Title: SWS101 Journal
categories: [SWS101, CTFjournal]
tags: [SWS101]
---

# Topic: Pickle Rick

This is a fun and short ctf challenge based on the Rick and Morty characters. It involves basic web exploitation and enumeration.

## Penetration Testing Methodology

* Network scanning (nmap scan)

* Enumeration
  - enumerating http service
  - extracting username from source codetry
  - directory bruteforce using dirb
  - extracting password from robots.txt
  - logging into the web application

* Exploitation 
  - exploiting command module
  - invoking reverse shell
  - extracting first and second ingredients
  - enumerating rick's file

* privelege excalation

## Walkthrough

Run a TCP nmap scan

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-20 14-26-58.png>)

The scan reveals that the target machine has 2 open ports: 22 and 80. 

Enumerating the http service

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-19-14.png>)

I inspected the source code of the web page and found a username: **R1ckRul3s**

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-21-27.png>)

Now i need to find hidden files or directories using gobuster

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-23-31.png>)

I found a hidden directory: **/login.php**. It takes us to a login page.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-25-08.png>)

When i tried the **/robots.txt** path, i found a password: **Wubbalubbadubdub**

So i login with the credentials and found a command panel that allows me to execute commands.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-30-35.png>)

We probably need to try and get a reverse shell. I tried to run a python reverse shell command but it didn't work. So i tried to use the command module to get a reverse shell.

Also try to find the first and second ingredients.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-32-05.png>)

When i tried to run a series of commands, like ls -la, i found a file named **Sup3rS3cretPickl3Ingred.txt**. I read the file and found the first ingredient.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-35-31.png>)

Tried to get source php code to get all blacklisted commands by putting ***grep -R***

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-37-46.png>)

source code
![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-38-43.png>)

ls seems to not be blacklisted. Check for sudo privileges using ***sudo -l***

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-40-32.png>)

I can run any command as sudo. So i ran ***sudo ls ../../../*** to find the second ingredient.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-41-33.png>)

Two flags found. 

/home/rick/second ingredients: 1 jerry tear
/root/third ingredients: fleeb juice

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-42-52.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-43-35.png>)

I got all the ingredients.