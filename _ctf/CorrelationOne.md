---
title: "CorrelationOne CTF Challenge: Hoasted Toasted"
layout: default
date: 2025-06-15
---
<link rel="stylesheet" href="/assets/css/custom.css">
## Recon Challenge
## Matthew McClintock 6/15/25
This is a walkthrough of 'Hoasted Toasted', one of the challenges in the 2025 CorrelationOne CTF Event hosted by the DoD.
This room was worth 150 points.

---

### 🧠 Challenge Description
<div class="highlight-box">
We are given a URL to begin and are tasked to locate the hidden internal-only site. 
</div>
<p align="center">
  <img src="/assets/images/44.png" alt="The challenges initial description" width="650">
</p>

---

### ✅ Steps Taken
<div class="highlight-box">
Upon visiting the URL, we are greeted with the following landing page.
</div>
<p align="center">
  <img src="/assets/images/2.png" alt="Landing page of the given URL" width="650">
</p>
<div class="highlight-box">
Theres nothing odd at first glance. No buttons to click on or anything to interact with. We can gather more information of the website by using <a href="https://www.ssllabs.com/ssltest/">SSLLabs</a>. 
This site is a free online tool by Qualys that analyzes the SSL/TLS configuration of websites. 

It can be useful for OSINT since we can gather things like server IP's, hosting providor info, certificate issuer, and Comman Name & Alternative Name's. The last of which will help us out here. 

We find that the alternative name is definitelynotaflag.north.torbia. Definitely not suspicious...
</div>
<p align="center">
  <img src="/assets/images/333.png" alt="SSLLabs info" width="650">
</p>

---
<div class="highlight-box">
Unfortunately, trying to visit that site directly does not work. The site will not resolve externally so we have to find a way to fix that. 
</div>
<p align="center">
  <img src="/assets/images/6.png" alt="Unresolved alt site" width="650">
</p>

---
<div class="highlight-box">
Luckily we can modify the /etc/hosts system file on our kali machine. /etc/hosts is a plain text file that locally maps IP addresses to hostnames. Its like a mini DNS server. It is not unique to Kali, but found on all Unix operating systems. 

Before we do that, we need to find the IP of the original site not-torbian.ethtrader-ai.com. 

We'll use the 'dig' command for that.
</div>
<p align="center">
  <img src="/assets/images/5.png" alt="dig command" width="650">
</p>

---
<div class="highlight-box">
We can see that the IP address is 34.86.60.228. Now that we have all this information, we can edit the /etc/hosts file I previously talked about.

We do this by editing the content with 'nano'. 
</div>
<p align="center">
  <img src="/assets/images/7.png" alt="nano command" width="650">
</p>
<div class="highlight-box">
As you can see there are only 2 entries. We'll add a 3rd.
</div>
<p align="center">
  <img src="/assets/images/8.png" alt="/etc/hosts content" width="650">
</p>

---
<div class="highlight-box">
Mapping 34.86.60.228 to the subdomain 'definitelynotaflag.north.torbia' should do the trick.
</div>
<p align="center">
  <img src="/assets/images/9.png" alt="/etc/hosts content" width="650">
</p>

---
<div class="highlight-box">
By adding a line in /etc/hosts to point 'definitelynotaflag.north.torbia' to the main site’s IP, the system bypassed DNS and sent the request directly to that IP.
The server saw the 'definitelynotaflag.north.torbia' hostname in the request (from the Host header) and responded with the correct hidden content, even though the IP was shared with the main site.

Now upon visiting the internal url, we can finally access the site! 
</div>
<p align="center">
  <img src="/assets/images/10.png" alt="internal site access" width="650">
</p>

---

### 🎯 Flag
<div class="highlight-box">
Among the secrets is the flag at the bottom!
</div>
<p align="center">
  <img src="/assets/images/111.png" alt="Flag found" width="650">
</p>

---


