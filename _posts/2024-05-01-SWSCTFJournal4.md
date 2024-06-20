---
Title: SWS101 Journal
categories: [SWS101, CTFjournal]
tags: [SWS101]
---

# Topic: Kenobi

This is a fun and short ctf challenge based on the Star Wars characters. It involves basic web exploitation and enumeration.

## Task 1: Deploy the machine

The first task is to deploy the machine and connect to the VPN. Once the machine is deployed, we can start the enumeration process. To find services running on the machine I am using Rustscan which is faster than nmap.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 00-52-04.png>)

## Task 2: Enumerating Samba for shares

There is SMB running on the machine. Start our attack by looking at SMB service.

Nmap gives scan results of the SMB service running on the machine. I can use smbclient to connect to the SMB service and list the shares.

3 shares are found: **anonymous, profiles, and share**. 

There is an anonymous share that allows us to list the contents of the share. I can connect to the share using smbclient and list the contents.

**log.txt** file is found in the share. I can download the file using the get command.

For downloading the file, I can use the **smbget** command.

Now that I have the log file, I can read the contents of the file.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 01-02-11.png>)

There is SSH private key in the log file. I can save the key in a file and use it to connect to the machine.

**FTP** is running on port 21.

I found some data in the SMB service. I can look at NFS to see if there is any data in the target.

