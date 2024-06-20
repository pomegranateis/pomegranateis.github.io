---
Title: SWS101 Journal
categories: [SWS101, CTFjournal]
tags: [SWS101]
---

# Topic: Cyborg

Run a nmap scan.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-00-23.png>)

Website page.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-01-45.png>)

For more recon, I will run dirsearch.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-03-16.png>)

I find two directories; /etc/ and /admin/

Looking at admin i see this page.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-08-14.png>)

Navigating to the /admin path I see this page as well.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-09-28.png>)

It seems like conversations between admin and a message from alex about how to set up proxy. 

In /etc/ we find,

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-11-16.png>)

Theres a squid directory, if we open it we found a passwd file with a hash

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-11-58.png>)

Now we can try to crack it using John the ripper

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-12-40.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-13-31.png>)

And we found a password: squidward

I tried to see if that was a password for ssh connection but it failed, so, after investigating further the website I found out that we can download a tar file form the dropdown menu on the admin page that we found

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-14-37.png>)

Now let’s run tar -xvf archive.tar to extract the files and directories of the .tar file

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-15-16.png>)

Now we can explore some files, let’s check out README

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-16-01.png>)

It seems like a Backup Borg repository, we have to install Borg, let’s use “sudo apt install borgbackup -y” to do so

After that we can list the repository using “borg list home/field/dev/final_archive

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-17-01.png>)

this is where the password we found comes into play

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-17-09.png>)

Now, in borg we can use the command “mount” to mount a Borg repository as a FUSE (Filesystem in Userspace) virtual file system. This feature allows us to browse the contents of a Borg repository as if it were a regular file system. We need to create a folder to store the repository also

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-17-18.png>)

Now we can navigate trought the repo like a file system, if we go to documents directory of the alex user, we can find the password for alex

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-17-31.png>)

Now we can obtain an ssh shell for the alex user with that credentials

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-17-38.png>)

For the privilege escalation the process is very straight forward, just run “sudo -l” and we can see that alex can run /etc/mp3backups/backup.sh as sudo, so we can echo the shebang into the backup.sh and run it as sudo

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 05-17-49.png>)