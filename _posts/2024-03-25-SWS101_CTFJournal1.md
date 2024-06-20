---
Title: SWS101 Journal
categories: [SWS101, CTFjournal]
tags: [SWS101]
---

# TryHackMe Cyberlens

Let us exploit the CyberLens web server and discover its hidden flags.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 16-31-05.png>)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 16-31-51.png>)

### Task 1 CyberLens

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 16-32-45.png>)


**Challenge Description**

*Welcome to the clandestine world of CyberLens, where shadows dance amidst the digital domain and metadata reveals the secrets that lie concealed within every image. As you embark on this thrilling journey, prepare to unveil the hidden matrix of information that lurks beneath the surface, for here at CyberLens, we make metadata our playground.*

*In this labyrinthine realm of cyber security, we have mastered the arcane arts of digital forensics and image analysis. Armed with advanced techniques and cutting-edge tools, we delve into the very fabric of digital images, peeling back layers of information to expose the unseen stories they yearn to tell.*

*Picture yourself as a modern-day investigator, equipped not only with technical prowess but also with a keen eye for detail. Our team of elite experts will guide you through the intricate paths of image analysis, where file structures and data patterns provide valuable insights into the origins and nature of digital artifacts.*

*At CyberLens, we believe that every pixel holds a story, and it is our mission to decipher those stories and extract the truth. Join us on this exciting adventure as we navigate the digital landscape and uncover the hidden narratives that await us at every turn.*

*Can you exploit the CyberLens web server and discover the hidden flags?*

If we carry out a full port nmap scan:

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 17-25-47.png>)

The ports open are 
* 80/tcp: Open HTTP (Apache httpd 2.4.57) — No CVE Found
* 135/tcp: Open Microsoft Windows RPC
* 139/tcp: Open Microsoft Windows netbios-ssn
* 445/tcp: Open Microsoft-DS
* 3389/tcp: Open Microsoft Terminal Services (RDP)

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 16-35-18.png>)
![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 16-35-35.png>)
-

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 16-50-48.png>)

Exploring the site, we can notice 'CyberLens Image Extractor'.

If we get into it it seems like it let us upload an image and grabs its metadata. Furthur exploring the source code leads us to the main javascript functions.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 17-20-28.png>)

I attempted uploaded images found in http://cyberlens.thm/images/ to the tool for hints, but no useful metadata was found.

![alt text](<../assets/img/tryhackme_ctf/Screenshot from 2024-06-11 16-58-12.png>)

The extractor seems to use a different port for its operations. Let's examine this further in the browser.

![alt text](<../assets/img/tryhackme_ctf/1_P6BQpVkR-TJtGONvv2aayQ.webp>)

So the first thing is to look for a CVE for this apache tika version.

Now launch Metasploit and search for *apache*.

