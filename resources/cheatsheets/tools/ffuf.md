---
title: "ffuf Cheatsheet"
section: resources
topic: cheatsheets
date_created: 2026-06-04
last_updated: 2026-06-04
tags: [ffuf, fuzzing, web, directory, cheatsheet]
---

# ffuf Cheatsheet

## Dasar

```bash
# Directory fuzzing (paling sering dipakai)
ffuf -u http://target.com/FUZZ -w /path/to/wordlist.txt

# Dengan ekstensi file
ffuf -u http://target.com/FUZZ -w wordlist.txt -e .php,.html,.txt

# Colorize output
ffuf -u http://target.com/FUZZ -w wordlist.txt -c
```

---

## Wordlist yang Sering Dipakai

```bash
# Di Kali Linux, wordlist sudah tersedia di:
/usr/share/wordlists/dirb/common.txt
/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
/usr/share/seclists/Discovery/Web-Content/common.txt
/usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt

# SecLists (install dulu kalau belum ada)
sudo apt install seclists
```

---

## Filter Output

```bash
# Filter berdasarkan status code (hide 404)
ffuf -u http://target.com/FUZZ -w wordlist.txt -fc 404

# Filter beberapa status code
ffuf -u http://target.com/FUZZ -w wordlist.txt -fc 404,403

# Filter berdasarkan ukuran response
ffuf -u http://target.com/FUZZ -w wordlist.txt -fs 1234

# Filter berdasarkan jumlah kata
ffuf -u http://target.com/FUZZ -w wordlist.txt -fw 12

# Match hanya status code tertentu
ffuf -u http://target.com/FUZZ -w wordlist.txt -mc 200,301,302
```

---

## POST Request & Parameter Fuzzing

```bash
# POST request
ffuf -u http://target.com/login -w wordlist.txt -X POST -d "username=FUZZ&password=test"

# Fuzz parameter value
ffuf -u "http://target.com/page?id=FUZZ" -w numbers.txt

# Fuzz header
ffuf -u http://target.com/ -w wordlist.txt -H "X-Custom-Header: FUZZ"

# Fuzz subdomain
ffuf -u http://FUZZ.target.com -w subdomains.txt
```

---

## Multiple Wordlist (Custom Keyword)

```bash
# Pakai dua wordlist dengan keyword berbeda
ffuf -u http://target.com/FUZZ1/FUZZ2 -w wordlist1.txt:FUZZ1 -w wordlist2.txt:FUZZ2

# Brute force login
ffuf -u http://target.com/login -X POST \
  -d "username=FUZZ&password=W2" \
  -w users.txt:FUZZ \
  -w passwords.txt:W2 \
  -fc 401
```

---

## Speed & Thread

```bash
# Jumlah thread (default: 40)
ffuf -u http://target.com/FUZZ -w wordlist.txt -t 50

# Rate limit (request per second)
ffuf -u http://target.com/FUZZ -w wordlist.txt -rate 100

# Delay antar request (millisecond)
ffuf -u http://target.com/FUZZ -w wordlist.txt -p 0.1
```

---

## Output

```bash
# Simpan ke file JSON
ffuf -u http://target.com/FUZZ -w wordlist.txt -o output.json -of json

# Simpan ke file CSV
ffuf -u http://target.com/FUZZ -w wordlist.txt -o output.csv -of csv

# Verbose
ffuf -u http://target.com/FUZZ -w wordlist.txt -v
```

---

## Kombinasi yang Sering Dipakai di CTF

```bash
# Directory scan dasar
ffuf -u http://target.com/FUZZ -w /usr/share/seclists/Discovery/Web-Content/common.txt -c -fc 404

# Scan dengan ekstensi
ffuf -u http://target.com/FUZZ -w /usr/share/wordlists/dirb/common.txt -e .php,.txt,.html -c -fc 404

# Subdomain enumeration
ffuf -u http://FUZZ.target.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -c

# Fuzz GET parameter
ffuf -u "http://target.com/page?FUZZ=value" -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt -c -fs 0
```

---

→ [Back to Tools](README.md)
