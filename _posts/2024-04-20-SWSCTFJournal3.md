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
  - extracting username from source code
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

