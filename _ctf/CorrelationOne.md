---
title: "Basic Web Exploitation Challenge"
date: 2025-06-15
---

## Basic Web Exploitation Challenge

This is a walkthrough of a simple CTF web challenge.

---

### 🧠 Challenge Description

We were given a login form that was vulnerable to SQL injection.

---

### ✅ Steps Taken

1. Found the login form at `/login.php`
2. Tested SQL injection payload `' OR 1=1 --` in the username field.
3. Gained access as admin.

---

### 🎯 Flag

