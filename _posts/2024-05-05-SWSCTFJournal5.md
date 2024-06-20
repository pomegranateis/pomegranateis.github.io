---
Title: SWS101 Journal
categories: [SWS101, CTFjournal]
tags: [SWS101]
---

# Topic: The Marketplace

***The sysadmin of The Marketplace, Michael, has given you access to an internal server of his, so you can pentest the marketplace platform he and his team has been working on. He said it still has a few bugs he and his team need to iron out.***

***Can you take advantage of this and will you be able to gain root access on his server?***

As always, spawn the machine and run a nmap scan.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 02-57-28.png>)

Launch the browser and head to the IP address of the machine. The website is a marketplace platform. I can register and login to the platform.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-00-05.png>)

Try logging in as admin.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-01-37.png>)

**User not found**

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-02-37.png>)

See if sign up works with a new user work.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-04-15.png>)

Returns a *signed up succesfully* message.

Now let me log in back with the same credentials.

And we get in.

I tried to create some new listings but realized they block tese type of requests but do not sanitize them. So I added an XSS script to see if it worked.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-07-02.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-07-45.png>)

I noticed we can actually send listings to admins.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-09-31.png>)

From what i saw in the hint box, I went onto *PayloadsAlltheThings* saw this payload.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-11-08.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-12-25.png>)

I started a listener on mhy machine.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-13-57.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-14-47.png>)

When i continued to report to admins, i got a response on my listener.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-16-30.png>)

I copied the cookie and use a cookie editor and changed my current token.

With the admin token, i could go in **/admin**.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-19-10.png>)

Upon clicking any one of the users, I saw that I could do a sql injection easily.

I tried appending ' at the back of the url.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-20-59.png>)

I again tried, but this time with a union injection.

**?user=-1 union select (user()),2,3,4 — -**

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-21-56.png>)

Now to determine the database.

**user=-1 union select (select group_concat(SCHEMA_NAME) from INFORMATION_SCHEMA.SCHEMATA),2,3,4 — -**

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-23-25.png>)

To get the tables out.

**user=-1 union select (select group_concat(TABLE_NAME) from INFORMATION_SCHEMA.TABLES where TABLE_SCHEMA = ‘marketplace’),2,3,4 — -**

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-24-37.png>)

I noticed the messages table.

**user=-1 union select group_concat(user_to, message_content), null, null, null from messages**

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-25-51.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-26-56.png>)

I got the flag in user.txt by running cat.

Run **sudo -l**

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-29-17.png>)

Generate netcat reverse shell payload on my machine.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-30-11.png>)

Inject payload into a script for backup.tar to run.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-31-21.png>)

Once opened, change the permissions of the files and run it.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-32-17.png>)

I get a shell on my listener.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-33-07.png>)

Heading to GTFObins, I found the command to let us break out of the docker and give us a root shell.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-33-59.png>)

I got in as root.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-21 03-34-44.png>)