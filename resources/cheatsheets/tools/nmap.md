---
title: "Nmap Cheatsheet"
section: resources
topic: cheatsheets
date_created: 2026-06-04
last_updated: 2026-06-04
tags: [nmap, network, scanning, cheatsheet]
---

# Nmap Cheatsheet

## Scan Dasar

```bash
# Scan satu target
nmap 192.168.1.1

# Scan dengan service version detection
nmap -sV 192.168.1.1

# Scan dengan default scripts
nmap -sC 192.168.1.1

# Kombinasi yang paling sering dipakai
nmap -sC -sV 192.168.1.1

# Scan + simpan output
nmap -sC -sV 192.168.1.1 -oN hasil.txt
```

---

## Port

```bash
# Scan semua port (1-65535)
nmap -p- 192.168.1.1

# Scan port tertentu
nmap -p 80,443,8080 192.168.1.1

# Scan range port
nmap -p 1-1000 192.168.1.1

# Scan port umum (top 1000)
nmap 192.168.1.1

# Hanya tampilkan port yang open
nmap --open 192.168.1.1
```

---

## Scan Type

```bash
# SYN scan (default, butuh root)
nmap -sS 192.168.1.1

# TCP connect scan (tidak butuh root)
nmap -sT 192.168.1.1

# UDP scan
nmap -sU 192.168.1.1

# Skip host discovery (langsung scan meski host tidak ping)
nmap -Pn 192.168.1.1

# Matikan DNS resolution (lebih cepat)
nmap -n 192.168.1.1
```

---

## Detection

```bash
# OS detection
nmap -O 192.168.1.1

# Aggressive scan (OS, version, scripts, traceroute)
nmap -A 192.168.1.1

# Deteksi versi lebih intensif
nmap -sV --version-intensity 9 192.168.1.1
```

---

## Scripts (NSE)

```bash
# Jalankan script kategori vuln
nmap --script=vuln 192.168.1.1

# Script spesifik
nmap --script=http-title 192.168.1.1

# Beberapa script sekaligus
nmap --script=http-title,http-headers 192.168.1.1

# Script untuk SMB
nmap --script=smb-enum-shares 192.168.1.1

# Script untuk brute force
nmap --script=ssh-brute 192.168.1.1
```

---

## Timing & Speed

```bash
# T0 sampai T5 (makin besar makin cepat, T4 biasanya aman)
nmap -T4 192.168.1.1

# T3 default, T4 untuk jaringan yang bagus
nmap -T3 192.168.1.1
```

---

## Output

```bash
# Output normal ke file
nmap -oN output.txt 192.168.1.1

# Output XML
nmap -oX output.xml 192.168.1.1

# Output semua format sekaligus
nmap -oA output 192.168.1.1

# Verbose
nmap -v 192.168.1.1
nmap -vv 192.168.1.1
```

---

## Kombinasi yang Sering Dipakai di CTF

```bash
# Initial recon, cepat
nmap -sC -sV -T4 --open 10.10.10.1 -oN initial.txt

# Full port scan
nmap -p- -T4 10.10.10.1 -oN allports.txt

# Setelah dapat port dari full scan, scan detail port itu
nmap -sC -sV -p 22,80,443,8080 10.10.10.1 -oN targeted.txt

# Kalau host tidak merespons ping
nmap -Pn -sC -sV 10.10.10.1
```

---

→ [Back to Tools](README.md)
