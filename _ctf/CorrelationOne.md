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
This site is a free online tool by Qualys that analyzes the SSL/TLS configuration of websites. It can be useful for OSINT since we can gather things like server IP's, hosting providor info, certificate issuer, and Comman Name & Alternative Name's. The last of which will help us out here. We find that the alternative name is definitelynotaflag.north.torbia. Definitely not suspicious...

<p align="center">
  <img src="/assets/images/33.png" alt="SSLLabs info" width="650">
</p>




---

### 🎯 Flag

