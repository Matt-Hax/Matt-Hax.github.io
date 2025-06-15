---
title: "CorrelationOne CTF Challenge: Hoasted Toasted"
layout: default
date: 2025-06-15
---

## Basic Web Exploitation Challenge

This is a walkthrough on 'Hoasted Toasted', one of the challenges in the 2025 CorrelationOne CTF Event hosted by the DoD.

---

### 🧠 Challenge Description

We are given a URL to begin and are tasked to locate the hidden internal-only site. 

<p align="center">
  <img src="/assets/images/Hosted_Toasted.png" alt="The challenges initial description" width="650">
</p>

---

### ✅ Steps Taken

Upon visiting the URL, we are greeted with the following landing page.

<p align="center">
  <img src="/assets/images/2.png" alt="Landing page of the given URL" width="650">
</p>

Theres nothing odd at first glance. No buttons to click on or anything to interact with. We can gather more information of the website by using <a href="https://www.ssllabs.com/ssltest/">SSLLabs</a>. 
This site is a free online tool by Qualys that analyzes the SSL/TLS configuration of websites. 

It can be useful for OSINT since we can gather things like server IP's, hosting providor info, certificate issuer, and Comman Name & Alternative Name's. The last of which will help us out here. 

We find that the alternative name is definitelynotaflag.north.torbia. Definitely not suspicious...

<p align="center">
  <img src="/assets/images/333.png" alt="SSLLabs info" width="650">
</p>

Unfortunately, trying to visit that site directly does not work. The site will not resolve externally so we have to find a way to fix that. 
<p align="center">
  <img src="/assets/images/6.png" alt="Unresolved alt site" width="650">
</p>

Luckily we can modify the /etc/hosts system file on our kali machine. /etc/hosts is a plain text file that locally maps IP addresses to hostnames.

Its like a mini DNS server. It is not unique to Kali, but found on all Unix operating systems. Before we do that, we need to find the IP of the original site not-torbian.ethtrader-ai.com. 

We'll use the 'dig' command for that.

<p align="center">
  <img src="/assets/images/5.png" alt="dig command" width="650">
</p>

We can see that the IP address is 34.86.60.228. Now that we have all this information, we can edit the /etc/hosts file I previously talked about.

We do this by editing the content with 'nano'. 

---

### 🎯 Flag

