---
title: "Burp Suite Cheatsheet"
section: resources
topic: cheatsheets
date_created: 2026-06-04
last_updated: 2026-06-04
tags: [burpsuite, web, proxy, cheatsheet]
---

# Burp Suite Cheatsheet

## Keyboard Shortcuts

| Shortcut | Fungsi |
|---|---|
| `Ctrl + R` | Kirim request ke Repeater |
| `Ctrl + I` | Kirim request ke Intruder |
| `Ctrl + S` | Kirim ke Scanner (Pro) |
| `Ctrl + Shift + R` | Buka Repeater tab |
| `Ctrl + Shift + I` | Buka Intruder tab |
| `Ctrl + Z` | Forward request di Intercept |
| `Ctrl + F` | Cari teks di request/response |
| `Ctrl + U` | URL encode selection |
| `Ctrl + Shift + U` | URL decode selection |
| `Ctrl + B` | Base64 encode selection |
| `Ctrl + Shift + B` | Base64 decode selection |

---

## Proxy Setup

**Di Burp:**
Proxy > Options > pastikan listener di `127.0.0.1:8080`

**Di Browser (Firefox):**
Settings > Network Settings > Manual Proxy
- HTTP Proxy: `127.0.0.1`
- Port: `8080`
- Centang "Use this proxy for all protocols"

**Install CA Certificate:**
1. Buka browser yang sudah di-proxy ke Burp
2. Akses `http://burp`
3. Download CA Certificate
4. Import ke browser: Firefox > Settings > Privacy & Security > Certificates > Import

---

## Intercept

Intercept adalah fitur untuk menangkap request sebelum dikirim ke server, sehingga lo bisa modifikasi dulu.

```
Proxy > Intercept > pastikan "Intercept is on"
```

**Yang bisa lo lakukan:**
- Ubah parameter (GET/POST)
- Ubah header (User-Agent, Cookie, dll)
- Ubah method (GET ke POST, dll)
- Drop request (batalkan)
- Forward (kirim request apa adanya)

**Intercept Response:**
Proxy > Options > Intercept Server Responses > centang sesuai kebutuhan

---

## Repeater

Repeater dipakai untuk kirim request yang sama berkali-kali dengan modifikasi berbeda, cocok untuk manual testing.

**Cara pakai:**
1. Intercept request
2. Klik kanan > Send to Repeater (`Ctrl + R`)
3. Modifikasi request di panel kiri
4. Klik Send
5. Lihat response di panel kanan

**Tips:**
- Bisa buka beberapa tab Repeater sekaligus
- Klik tanda + di tab bar untuk rename tab
- History request tersimpan, bisa navigate mundur

---

## Intruder

Intruder dipakai untuk automated attack dengan payload list. Ada 4 attack type:

**Sniper (paling sering dipakai)**
Satu wordlist, satu posisi. Coba setiap payload satu per satu di posisi yang dipilih. Cocok untuk brute force satu parameter.

**Cluster Bomb**
Beberapa wordlist, beberapa posisi. Coba semua kombinasi. Cocok untuk brute force username + password.

**Pitchfork**
Beberapa wordlist, beberapa posisi. Pasang satu per satu secara bersamaan (bukan kombinasi). Cocok kalau username dan password sudah dipasangkan.

**Battering Ram**
Satu wordlist, beberapa posisi. Payload yang sama dimasukkan ke semua posisi sekaligus.

**Cara pakai:**
1. Intercept atau kirim request ke Intruder (`Ctrl + I`)
2. Tab Positions: highlight parameter yang mau di-fuzz, klik Add
3. Tab Payloads: masukkan wordlist atau payload list
4. Klik Start Attack

---

## Decoder

Tool untuk encode/decode data dengan cepat.

**Yang tersedia:**
- URL encode / decode
- HTML encode / decode
- Base64 encode / decode
- Hex encode / decode
- ASCII hex
- Gzip

**Cara pakai:**
Highlight teks di request/response > klik kanan > Send to Decoder

---

## Target dan Sitemap

**Site Map:**
Target > Site Map menampilkan semua URL yang sudah pernah lewat Burp.

Klik kanan URL > Spider this host (Community) atau Scan (Pro) untuk enumerate lebih lanjut.

**Scope:**
Target > Scope: definisikan domain/URL yang lo mau test. Request di luar scope tidak masuk Proxy history.

---

## Tips Umum

**Filter di Proxy History:**
HTTP History > klik Filter bar > bisa filter by status code, MIME type, atau keyword tertentu.

**Match and Replace:**
Proxy > Options > Match and Replace: otomatis ganti string tertentu di setiap request/response. Berguna untuk ganti User-Agent atau tambah header secara otomatis.

**Highlight Request Penting:**
Klik kanan request di HTTP History > Highlight: tandai warna untuk request yang penting agar mudah ditemukan lagi.

**Comparer:**
Kirim dua response ke Comparer untuk lihat perbedaannya secara visual. Berguna untuk blind SQLi atau testing autentikasi.

---

→ [Back to Tools](README.md)
