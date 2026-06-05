---
title: "KPU Data Breach (2023): 204 Juta Data Pemilih Bocor Jelang Pemilu"
section: case-studies
category: breaches
organization: Komisi Pemilihan Umum (KPU) Indonesia
date_incident: 2023-11
date_created: 2026-06-04
last_updated: 2026-06-04
status: published
language: id-en (bilingual mixed)
tags: [data-breach, indonesia, KPU, pemilu, government, 2023, election-security]
---

# KPU Data Breach (2023): 204 Juta Data Pemilih Bocor Jelang Pemilu

**Organisasi:** Komisi Pemilihan Umum (KPU) Republik Indonesia
**Tanggal Terdeteksi:** November 2023
**Pelaku:** Hacker dengan alias "Jimbo"
**Skala:** 252 juta records diklaim (204 juta unik setelah deduplication)
**Kategori:** Data breach, unauthorized access, data exfiltration

Tiga bulan sebelum Indonesia menggelar Pemilu serentak 2024, salah satu kebocoran data terbesar dalam sejarah pemilihan umum Indonesia terjadi. Seorang hacker bernama "Jimbo" mengklaim berhasil mengambil data dari sistem KPU dan menawarkannya di BreachForums seharga $74.000. Data yang bocor mencakup informasi pemilih dari seluruh Indonesia.

Bukan sekadar data biasa. Ini adalah data DPT (Daftar Pemilih Tetap), database yang menjadi fondasi legitimasi sebuah pemilihan umum.

---

## Latar Belakang

KPU (Komisi Pemilihan Umum) adalah lembaga negara yang bertanggung jawab atas penyelenggaraan pemilihan umum di Indonesia. Untuk Pemilu 2024, KPU mengelola data ratusan juta pemilih dalam sistem yang disebut SIDALIH (Sistem Informasi Data Pemilih).

SIDALIH menyimpan informasi demografis lengkap tentang setiap pemilih terdaftar di seluruh Indonesia. Data ini digunakan untuk proses verifikasi pemilih, distribusi surat suara, dan penentuan TPS (Tempat Pemungutan Suara).

Pemilu 2024 adalah salah satu pemilihan paling kompleks yang pernah diselenggarakan di Indonesia: memilih Presiden, DPR, DPD, DPRD Provinsi, dan DPRD Kabupaten/Kota secara serentak pada 14 Februari 2024.

---

## Timeline

| Tanggal | Kejadian |
|---|---|
| November 2023 | Akun "Jimbo" di BreachForums mengklaim memiliki 252 juta records data pemilih KPU |
| November 2023 | Sample data dipublikasikan sebagai bukti, terverifikasi mengandung data pemilih nyata |
| November 2023 | KPU mengakui adanya "dugaan kebocoran" dan memulai investigasi |
| November 2023 | Bareskrim Polri mulai penyelidikan |
| Desember 2023 | KPU menyatakan sistem pemilihan tidak terganggu |
| Desember 2023 | Data lengkap ditawarkan di BreachForums seharga $74.000 |
| 14 Februari 2024 | Pemilu 2024 tetap dilaksanakan |
| 2024 | Investigasi berlanjut, pelaku belum berhasil ditangkap secara publik |

---

## Data yang Bocor

Berdasarkan sample yang dipublikasikan oleh "Jimbo" sebagai bukti, data yang diklaim bocor mencakup:

- Nomor Induk Kependudukan (NIK)
- Nomor Kartu Keluarga (KK)
- Nama lengkap
- Tempat dan tanggal lahir
- Jenis kelamin
- Alamat lengkap (RT/RW, kelurahan, kecamatan, kabupaten/kota, provinsi)
- Nomor TPS
- Status disabilitas

Sample yang dipublikasikan diverifikasi oleh beberapa peneliti dan jurnalis sebagai data valid, dengan mencocokkan sebagian data dengan informasi publik yang dapat diverifikasi.

Angka 252 juta turun menjadi sekitar 204 juta records unik setelah menghilangkan duplikasi. Jumlah ini masih sangat besar, mewakili hampir seluruh pemilih terdaftar Indonesia.

---

## Bagaimana Ini Terjadi

Seperti kasus BPJS Kesehatan, KPU tidak pernah mengeluarkan disclosure teknis yang transparan tentang bagaimana persis akses ini bisa terjadi. Berdasarkan analisis komunitas keamanan siber:

**Akses ke sistem SIDALIH:** Data yang bocor sangat terstruktur dan lengkap, mengindikasikan akses langsung ke database atau sistem backend, bukan sekadar scraping data publik.

**Kemungkinan credential compromise:** Akses ke skala data sebesar ini biasanya memerlukan kredensial yang valid atau eksploitasi vulnerability signifikan pada sistem yang terhubung ke database.

**Timing yang mencurigakan:** Insiden ini terjadi dalam periode politik yang sangat sensitif. Apakah ini serangan oportunistis atau ada motivasi spesifik terkait Pemilu: pertanyaan ini tidak pernah terjawab secara definitif.

---

## Dimensi yang Membuat Ini Berbeda

Kebocoran data pemilih bukan hanya privacy violation. Ada dimensi khusus yang membuatnya lebih serius dibanding kebocoran data biasa:

**Legitimasi proses demokrasi**
DPT adalah dokumen fondasi pemilihan umum. Kekhawatiran segera muncul: apakah integritas data pemilih masih terjaga? Apakah ada manipulasi terhadap data, bukan sekadar pencurian? Pertanyaan ini, meski KPU membantah ada manipulasi, sulit dijawab dengan meyakinkan tanpa audit independen yang transparan.

**Potensi untuk disinformasi**
Data pemilih yang bocor bisa digunakan untuk membuat narasi disinformasi tentang proses pemilu: klaim data pemilih fiktif, manipulasi daftar pemilih, dan sejenisnya. Terlepas dari kebenarannya, keberadaan data yang bocor memberikan amunisi untuk narratif semacam itu.

**Targeting berbasis lokasi**
Data ini mencakup informasi TPS setiap pemilih. Dengan data ini, dimungkinkan untuk memetakan distribusi demografis pemilih di tingkat RT/RW, informasi yang bisa dieksploitasi untuk berbagai kepentingan politik.

**Tidak ada cara untuk "menarik kembali" data pemilih**
NIK, nama, alamat, tanggal lahir adalah data yang tidak bisa diganti seperti password. Orang tidak bisa mengganti NIK mereka karena datanya bocor. Dampaknya bersifat permanen.

---

## Respons

### KPU
KPU mengakui adanya dugaan kebocoran dan menyatakan sedang melakukan investigasi. Mereka juga menyatakan bahwa sistem pemungutan suara tidak terganggu dan integritas proses pemilu terjaga. Namun seperti kasus kebocoran data Indonesia lainnya, tidak ada disclosure teknis yang detail tentang apa yang terjadi dan bagaimana mencegahnya terulang.

### Penegak Hukum
Bareskrim Polri membuka penyelidikan. Pelaku "Jimbo" sejauh ini tidak berhasil diidentifikasi atau ditangkap secara publik.

### Pemilu 2024
Pemilu 2024 tetap dilaksanakan pada 14 Februari 2024 dan berjalan tanpa gangguan teknis yang signifikan pada hari pemungutan suara. Namun pertanyaan tentang keamanan data pemilih tetap menjadi catatan serius untuk pemilu mendatang.

---

## Konteks: Tren Serangan terhadap Sistem Pemilu Global

Insiden KPU bukan terjadi dalam vakum. Secara global, sistem pemilu dan infrastruktur demokrasi semakin menjadi target serangan siber:

- Amerika Serikat mengalami upaya interference pada Pemilu 2016 yang terdokumentasi dengan baik
- Beberapa negara Eropa mengalami serangan DDoS terhadap sistem pemungutan suara online
- Filipina mengalami kebocoran data pemilih skala besar pada 2016

Tren ini mencerminkan satu realitas: infrastruktur demokrasi adalah target yang sangat bernilai bagi aktor yang ingin mendestabilisasi suatu negara.

---

## Pelajaran yang Bisa Diambil

**Sistem yang menyimpan data kritis nasional butuh standar keamanan setara dengan infrastruktur kritis.**
Data pemilih bukan sekadar database administratif. Ini adalah fondasi legitimasi demokrasi. Standar keamanannya seharusnya mencerminkan nilai politisnya, bukan hanya nilai teknis datanya.

**Timing insiden memiliki dampak yang jauh melebihi datanya sendiri.**
Kebocoran data pemilih tiga bulan sebelum pemilu tidak hanya membahayakan privasi individu. Ini membuka ruang untuk narratif disinformasi tentang integritas proses demokratis.

**Transparansi dalam insiden yang melibatkan kepentingan publik bukan pilihan, itu kewajiban.**
Ketika data yang bocor adalah data yang dikumpulkan atas nama negara, untuk kepentingan proses kenegaraan, maka penjelasan yang transparan kepada publik adalah tanggung jawab yang tidak bisa dihindari.

**Indonesia perlu security audit independen untuk sistem pemilu.**
Audit keamanan oleh pihak ketiga yang kompeten dan independen terhadap SIDALIH dan sistem KPU lainnya adalah langkah yang masuk akal pasca insiden ini. Pernyataan internal dari KPU bahwa "sistem aman" tidak cukup sebagai jaminan.

**Data kependudukan yang tidak bisa diubah membutuhkan perlindungan yang lebih ketat.**
NIK, nama, dan tanggal lahir adalah data seumur hidup. Ketika bocor, dampaknya bersifat permanen. Ini seharusnya mendorong standar perlindungan yang jauh lebih tinggi untuk jenis data ini dibanding data yang bisa di-reset seperti password.

---

## Key Takeaways

- 204 juta data pemilih unik bocor dari sistem KPU pada November 2023, tiga bulan sebelum Pemilu 2024.
- Data yang bocor mencakup NIK, nama, alamat lengkap, tanggal lahir, dan nomor TPS: informasi yang tidak bisa diganti.
- Hacker "Jimbo" menawarkan data ini di BreachForums seharga $74.000.
- KPU mengakui dugaan kebocoran tapi tidak memberikan disclosure teknis yang transparan.
- Tidak ada pelaku yang berhasil ditangkap secara publik.
- Kebocoran data pemilih memiliki dimensi yang melampaui privacy violation biasa: ia menyentuh legitimasi proses demokrasi.
- Pemilu 2024 tetap berjalan, tapi pertanyaan tentang keamanan infrastruktur pemilu Indonesia belum terjawab secara memuaskan.

---

## Sources

- [Laporan awal BreachForums (archived)](https://breachforums.is) - klaim awal "Jimbo"
- [Kompas: Kronologi Dugaan Kebocoran Data KPU](https://www.kompas.com) - liputan kejadian
- [Tempo: Analisis Data Pemilih yang Bocor](https://www.tempo.co) - verifikasi sample data
- [KPU: Pernyataan Resmi Kebocoran Data](https://www.kpu.go.id) - respons resmi KPU
- [Bareskrim Polri: Penyelidikan Kasus KPU](https://www.polri.go.id) - tindak lanjut hukum

---

*case-studies / breaches · Dibuat: 2026-06-04*
