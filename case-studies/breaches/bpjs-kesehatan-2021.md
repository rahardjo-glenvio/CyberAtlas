---
title: "BPJS Kesehatan Data Breach (2021)"
section: case-studies
category: breaches
organization: BPJS Kesehatan
date_incident: 2021-05
date_created: 2026-06-04
last_updated: 2026-06-04
status: published
language: id-en (bilingual mixed)
tags: [data-breach, indonesia, BPJS, pemerintah, healthcare, 2021]
---

# BPJS Kesehatan Data Breach (2021)

**Organisasi:** BPJS Kesehatan (Badan Penyelenggara Jaminan Sosial Kesehatan)
**Tanggal:** Mei 2021
**Skala:** 279 juta records diklaim bocor
**Kategori:** Data breach, unauthorized access, data leak

Pada Mei 2021, sebuah akun dengan nama "Kotz" di forum hacker Raid Forums mengklaim memiliki data 279 juta penduduk Indonesia yang berasal dari sistem BPJS Kesehatan, dan menawarkan seluruh dataset itu seharga $6.000. Untuk perspektif: populasi Indonesia saat itu sekitar 273 juta jiwa. Angka 279 juta berarti data yang bocor mencakup orang yang sudah meninggal pun ikut terdaftar.

Ini bukan insiden biasa. Ini adalah salah satu kebocoran data terbesar dalam sejarah Indonesia, yang menyentuh hampir setiap warga negara secara langsung.

---

## Latar Belakang

BPJS Kesehatan adalah badan penyelenggara jaminan kesehatan nasional yang dibentuk berdasarkan UU No. 24 Tahun 2011. Per 2021, BPJS Kesehatan memiliki sekitar 222 juta peserta aktif, menjadikannya salah satu program asuransi kesehatan terbesar di dunia berdasarkan jumlah peserta.

Sebagai pengelola program jaminan kesehatan nasional, BPJS Kesehatan menyimpan data yang sangat sensitif tentang hampir seluruh penduduk Indonesia: data identitas, data medis, data kepesertaan, hingga informasi gaji untuk keperluan iuran.

Pada saat insiden ini terjadi, Indonesia belum memiliki undang-undang perlindungan data pribadi yang komprehensif. UU PDP baru disahkan pada Oktober 2022, setahun setelah kebocoran ini terjadi.

---

## Timeline

| Tanggal | Kejadian |
|---|---|
| 20 Mei 2021 | Akun "Kotz" di Raid Forums mengumumkan memiliki 279 juta records data BPJS |
| 20 Mei 2021 | Sample data sebanyak 1 juta records dibagikan gratis sebagai bukti |
| 21 Mei 2021 | Berita menyebar di media Indonesia, publik mulai panik |
| 21 Mei 2021 | BPJS Kesehatan menyatakan sedang melakukan "penelusuran" |
| 22 Mei 2021 | Kominfo meminta Raid Forums menurunkan postingan tersebut |
| 24 Mei 2021 | BPJS Kesehatan mengakui ada kemungkinan kebocoran tapi tidak mengkonfirmasi skala |
| Mei 2021 | Raid Forums menghapus listing setelah tekanan dari pemerintah Indonesia |
| 2022 | Tidak ada pelaku yang berhasil diidentifikasi secara publik |

---

## Data yang Bocor

Berdasarkan sample yang dibagikan secara publik, data yang diklaim bocor mencakup:

- Nomor Induk Kependudukan (NIK)
- Nomor Kartu Keluarga (KK)
- Nama lengkap
- Alamat
- Nomor telepon
- Email
- Tanggal lahir
- Jenis kelamin
- Informasi gaji (untuk peserta mandiri dengan iuran berbasis gaji)
- Status kepesertaan

Data ini adalah kombinasi yang sangat berbahaya. NIK + nama + tanggal lahir + alamat sudah cukup untuk membuat identitas palsu, mengajukan pinjaman online atas nama korban, atau melakukan social engineering yang sangat targeted.

---

## Bagaimana Ini Terjadi

Hingga hari ini, tidak ada disclosure resmi dari BPJS Kesehatan tentang bagaimana persis kebocoran ini terjadi. Ini sendiri adalah masalah yang signifikan dari perspektif akuntabilitas.

Dari analisis yang dilakukan peneliti dan komunitas keamanan siber, beberapa hipotesis yang beredar:

**Akses database langsung:** Data yang bocor terlihat sangat terstruktur dan lengkap, mengindikasikan kemungkinan akses langsung ke database production, bukan hanya scraping dari antarmuka publik.

**Insider threat atau credential yang bocor:** Skala data yang bisa diakses mengindikasikan kemungkinan akses menggunakan kredensial legitimate, baik yang dicuri maupun dari orang dalam.

**Kelemahan pada sistem API atau antarmuka internal:** Beberapa peneliti menduga ada endpoint yang tidak terlindungi dengan baik yang memungkinkan enumerasi data dalam jumlah besar.

Tidak ada satu pun hipotesis ini yang dikonfirmasi secara resmi.

---

## Dampak

### Skala
279 juta records adalah angka yang hampir tidak bisa dimengerti secara intuitif. Untuk perspektif: ini setara dengan seluruh penduduk Indonesia, ditambah puluhan juta orang yang sudah meninggal tapi datanya masih tersimpan di sistem.

### Untuk Individu
Setiap orang yang terdaftar di BPJS Kesehatan berpotensi terdampak. Data yang bocor cukup untuk:
- Membuat identitas palsu
- Mengajukan pinjaman online (pinjol) atas nama korban
- Melakukan phishing yang sangat dipersonalisasi
- Social engineering terhadap korban atau keluarganya

### Untuk Kepercayaan Publik
Insiden ini terjadi pada program yang bersifat wajib. Warga negara tidak punya pilihan untuk tidak mendaftarkan diri ke BPJS Kesehatan. Ketika data dari program wajib bocor tanpa akuntabilitas yang jelas, ini adalah kegagalan kepercayaan publik yang sangat serius.

### Finansial
Tidak ada laporan biaya resmi dari BPJS Kesehatan terkait insiden ini. Seller menawarkan seluruh dataset seharga $6.000, sebuah angka yang mengejutkan kecil mengingat nilai potensial data tersebut di tangan yang salah.

---

## Respons

### BPJS Kesehatan
Respons BPJS Kesehatan dinilai oleh banyak pihak sebagai tidak memadai. Tidak ada konfirmasi eksplisit tentang skala kebocoran, tidak ada notifikasi ke peserta yang terdampak, dan tidak ada disclosure detail tentang bagaimana kebocoran terjadi atau apa langkah perbaikan yang diambil.

### Pemerintah
Kominfo meminta platform Raid Forums untuk menurunkan posting tersebut. Posting berhasil diturunkan, tapi data yang sudah tersebar tidak bisa ditarik kembali. Pendekatan "turunkan postingnya" tanpa menangani akar masalahnya adalah respons yang bersifat reaktif dan kosmetik.

### Hukum
Tidak ada tuntutan hukum yang berhasil dilakukan terhadap pelaku. Tidak ada pelaku yang diidentifikasi secara publik.

---

## Pelajaran yang Bisa Diambil

**Kebocoran data tidak bisa "diturunkan" seperti postingan media sosial.**
Begitu data tersebar, langkah yang relevan adalah mitigasi dampak, bukan menghapus buktinya. Meminta platform untuk menurunkan listing tidak melindungi satu pun warga yang datanya sudah beredar.

**Program wajib membawa tanggung jawab keamanan yang lebih tinggi.**
Ketika warga negara tidak punya pilihan untuk tidak memberikan datanya, organisasi yang menyimpan data itu punya kewajiban yang jauh lebih tinggi untuk melindunginya. Tidak ada justifikasi untuk keamanan yang longgar ketika data bersifat wajib dan skala penyimpanannya nasional.

**Tidak ada disclosure bukan berarti tidak ada kebocoran.**
BPJS Kesehatan tidak pernah secara eksplisit mengkonfirmasi atau menjelaskan insiden ini secara transparan. Absennya komunikasi resmi yang jelas adalah kegagalan tersendiri, terlepas dari kegagalan teknisnya.

**Indonesia tidak punya kerangka hukum yang memadai saat insiden ini terjadi.**
UU PDP yang disahkan Oktober 2022 memang sebagian terinspirasi oleh serangkaian insiden kebocoran data besar di Indonesia, termasuk kasus BPJS ini. Ironisnya, undang-undang itu hadir setelah kerusakannya terjadi.

**Data lama tetap berbahaya.**
Data yang bocor pada 2021 masih bisa digunakan untuk fraud, social engineering, dan identity theft bertahun-tahun setelahnya. Kebocoran data tidak memiliki "expiry date."

---

## Relevansi dengan UU PDP

Insiden BPJS ini menjadi salah satu argumen terkuat mengapa Indonesia membutuhkan UU PDP yang komprehensif. Berdasarkan UU PDP yang berlaku sejak Oktober 2024:

- BPJS Kesehatan sebagai data controller wajib melaporkan kebocoran ke lembaga pengawas dalam 14 x 24 jam
- Peserta yang terdampak berhak mendapat notifikasi
- Ada sanksi administratif hingga 2% pendapatan tahunan untuk kegagalan keamanan

Kalau UU PDP sudah berlaku saat insiden ini terjadi, BPJS Kesehatan akan menghadapi kewajiban hukum yang jauh lebih ketat.

Baca lebih lanjut tentang UU PDP di: [UU PDP Indonesia](../../laws-and-privacy/data-protection/uu-pdp-indonesia.md)

---

## Key Takeaways

- 279 juta records BPJS Kesehatan bocor pada Mei 2021, dijual di forum hacker seharga $6.000.
- Data yang bocor mencakup NIK, nama, alamat, telepon, dan informasi gaji, kombinasi yang cukup untuk identity theft dan fraud.
- Tidak ada disclosure resmi yang transparan dari BPJS Kesehatan tentang bagaimana kebocoran terjadi.
- Respons pemerintah bersifat kosmetik: meminta platform menghapus postingan, bukan menangani akar masalahnya.
- Tidak ada pelaku yang berhasil diidentifikasi dan dituntut secara publik.
- Insiden ini menjadi salah satu katalis untuk pengesahan UU PDP pada 2022.

---

## Sources

- [Laporan awal Raid Forums (archived)](https://web.archive.org) - posting asli sebelum diturunkan
- [CNN Indonesia: BPJS Kesehatan Data Breach Coverage](https://www.cnnindonesia.com) - liputan berita Mei 2021
- [Kominfo: Tindak lanjut kebocoran data BPJS](https://www.kominfo.go.id) - respons resmi pemerintah
- [Kompas: Kronologi Dugaan Kebocoran Data BPJS](https://www.kompas.com) - timeline kejadian
- Have I Been Pwned - verifikasi sample data

---

*case-studies / breaches · Dibuat: 2026-06-04*
