---
title: "Bank BSI Ransomware Attack (2023)"
section: case-studies
category: breaches
organization: Bank Syariah Indonesia (BSI)
date_incident: 2023-05
date_created: 2026-06-04
last_updated: 2026-06-04
status: published
language: id-en (bilingual mixed)
tags: [ransomware, indonesia, bank-bsi, lockbit, financial-sector, 2023]
---

# Bank BSI Ransomware Attack (2023)

**Organisasi:** PT Bank Syariah Indonesia Tbk (BSI)
**Tanggal:** 8 Mei 2023
**Pelaku:** LockBit 3.0 ransomware group
**Skala:** 1,5 TB data diklaim dicuri, 15 juta data nasabah
**Kategori:** Ransomware, data exfiltration, double extortion

Senin pagi, 8 Mei 2023. Jutaan nasabah Bank BSI mencoba mengakses mobile banking atau menarik uang lewat ATM. Tidak bisa. Sistem tidak merespons. BSI menyebut ini "gangguan teknis" yang sedang dalam perbaikan.

Empat hari kemudian, kelompok ransomware LockBit 3.0 mengklaim bertanggung jawab atas lumpuhnya sistem bank syariah terbesar Indonesia itu. Mereka bilang sudah mencuri 1,5 terabyte data, termasuk data 15 juta nasabah, informasi karyawan, dan dokumen internal. Dan mereka memberi ultimatum: bayar tebusan, atau data itu dipublikasikan.

---

## Latar Belakang

Bank Syariah Indonesia adalah bank syariah terbesar di Indonesia, dibentuk dari hasil merger tiga bank syariah milik BUMN: Bank Syariah Mandiri, BNI Syariah, dan BRI Syariah, yang resmi bergabung pada 2021. Per 2023, BSI memiliki lebih dari 15 juta nasabah dan aset sekitar Rp 350 triliun.

LockBit adalah salah satu kelompok ransomware paling aktif dan berbahaya di dunia. Mereka beroperasi dengan model Ransomware-as-a-Service (RaaS): kelompok inti mengembangkan ransomware, sementara "affiliate" menyebarkannya ke target dan berbagi keuntungan dari tebusan. LockBit 3.0 adalah versi ketiga dari malware mereka, diluncurkan 2022 dengan fitur evasion yang lebih canggih.

---

## Timeline

| Tanggal | Kejadian |
|---|---|
| 8 Mei 2023 | Layanan BSI mulai tidak bisa diakses, ATM dan mobile banking down |
| 8-9 Mei 2023 | BSI menyebut ini "pemeliharaan sistem" dan "gangguan teknis" |
| 11 Mei 2023 | Layanan BSI mulai pulih sebagian |
| 12 Mei 2023 | LockBit 3.0 mengklaim serangan dan mengumumkan deadline negosiasi |
| 15 Mei 2023 | Pakar keamanan Teguh Aprianto mengkonfirmasi serangan ransomware |
| 18 Mei 2023 | Deadline LockBit lewat tanpa pembayaran |
| 20 Mei 2023 | LockBit mulai publish sebagian data yang diklaim dicuri dari BSI |
| Mei-Juni 2023 | Investigasi berlanjut, BSI tidak mengkonfirmasi detail teknis serangan |

---

## Apa yang Terjadi

### Awal Serangan

Pada dini hari 8 Mei 2023, sistem BSI mulai terdampak. Berdasarkan analisis dari komunitas keamanan siber Indonesia, LockBit berhasil masuk ke jaringan internal BSI dan menyebarkan ransomware yang mengenkripsi data di banyak sistem sekaligus.

Proses ini tidak terjadi dalam semalam. Seperti kebanyakan ransomware attack modern, LockBit kemungkinan sudah berada di dalam jaringan BSI selama beberapa waktu sebelum mengaktifkan enkripsi, fase yang disebut "dwell time." Selama periode ini, mereka melakukan reconnaissance, lateral movement, dan exfiltration data sebelum enkripsi dimulai.

### Double Extortion

LockBit menggunakan taktik yang disebut double extortion: tidak hanya mengenkripsi data sehingga korban tidak bisa mengaksesnya, tapi juga mencuri data sebelum enkripsi, lalu mengancam akan mempublikasikannya kalau tebusan tidak dibayar.

Ini artinya bahkan jika BSI berhasil memulihkan data dari backup, ancaman kebocoran data nasabah tetap ada. Korban terjebak di antara dua pilihan yang sama-sama buruk.

### Data yang Diklaim Dicuri

LockBit mengklaim memiliki:
- Data pribadi 15 juta nasabah BSI
- Password dan PIN akun
- Informasi karyawan BSI
- Dokumen perjanjian dengan mitra
- Dokumen keuangan internal
- Total 1,5 TB data

Untuk membuktikan klaim mereka, LockBit mempublikasikan sample berupa screenshots dokumen internal BSI.

### Respons BSI

BSI konsisten tidak mengakui bahwa ini adalah serangan ransomware selama beberapa hari pertama. Komunikasi publik mereka menggunakan frasa "gangguan teknis" dan "pemeliharaan sistem," sebuah framing yang sangat berbeda dari kenyataan yang terjadi.

Ketika LockBit secara terbuka mengklaim serangan dan komunitas keamanan siber mulai mengkonfirmasi, baru BSI mulai mengakui adanya "masalah keamanan siber."

---

## Dampak

### Untuk Nasabah
Selama beberapa hari, jutaan nasabah BSI tidak bisa:
- Mengakses mobile banking
- Menarik uang dari ATM
- Melakukan transfer
- Menggunakan QRIS

Bagi sebagian nasabah yang bergantung pada BSI sebagai satu-satunya rekening, ini adalah krisis yang sangat nyata. Gaji tidak bisa dicairkan, tagihan tidak bisa dibayar, kebutuhan sehari-hari terhambat.

### Untuk Kepercayaan Sektor Perbankan
BSI adalah bank BUMN, bank milik negara. Lumpuhnya layanan selama berhari-hari, dikombinasi dengan komunikasi yang tidak transparan, menciptakan pertanyaan serius tentang ketangguhan sistem perbankan nasional terhadap ancaman siber.

### Potensi Eksposur Data
Data yang diklaim bocor termasuk data yang sangat sensitif: PIN, password, dan informasi keuangan. Meskipun BSI tidak pernah mengkonfirmasi secara spesifik data apa yang benar-benar berhasil dicuri, nasabah yang terdampak berisiko mengalami fraud, phishing yang dipersonalisasi, dan penyalahgunaan identitas.

---

## Analisis: Kenapa BSI?

Bank adalah target ransomware yang sangat menarik karena beberapa alasan:

**Willingness to pay:** Bank punya insentif yang sangat kuat untuk memulihkan layanan secepat mungkin. Setiap jam downtime adalah kerugian finansial dan reputasi yang sangat nyata. Ini meningkatkan kemungkinan tebusan dibayar.

**Critical data:** Bank menyimpan data keuangan dan identitas yang sangat bernilai, baik untuk dijual maupun sebagai leverage negosiasi.

**Kompleksitas sistem:** Sistem perbankan besar terdiri dari ratusan sistem yang saling terhubung, banyak yang dibangun di atas teknologi lama. Patching dan monitoring di seluruh surface attack yang besar ini adalah tantangan yang signifikan.

**Reputasi sebagai leverage:** Publikasi data nasabah tidak hanya merusak korban, tapi juga merusak reputasi bank. Ancaman ini sangat efektif sebagai tekanan tambahan.

---

## Tentang LockBit

LockBit adalah salah satu kelompok ransomware paling produktif secara global. Beberapa fakta:

- Bertanggung jawab atas lebih dari 1.700 serangan ransomware di seluruh dunia per 2023
- Beroperasi dengan model RaaS, memungkinkan affiliate tanpa keahlian teknis tinggi untuk melancarkan serangan
- Target mereka mencakup rumah sakit, pemerintah, perusahaan Fortune 500, hingga bank
- Pada Februari 2024, operasi LockBit berhasil di-takedown oleh operasi gabungan FBI, Europol, dan law enforcement dari 10 negara lainnya
- Beberapa bulan kemudian, LockBit kembali beroperasi di bawah nama yang sama

BSI adalah salah satu korban paling publik dari LockBit di Asia Tenggara.

---

## Pelajaran yang Bisa Diambil

**Komunikasi krisis yang tidak jujur memperburuk situasi.**
Menyebut ransomware attack sebagai "gangguan teknis" tidak melindungi bank dari dampaknya, justru merusak kepercayaan lebih dalam ketika kenyataan akhirnya terungkap. Transparansi dalam komunikasi krisis, meski menyakitkan secara reputasi jangka pendek, jauh lebih baik daripada menyembunyikan fakta.

**Ransomware modern bukan sekadar enkripsi.**
Double extortion mengubah kalkulasi respons insiden secara fundamental. Backup yang bagus menyelesaikan masalah availability, tapi tidak menyelesaikan masalah confidentiality. Organisasi perlu punya rencana untuk kedua skenario tersebut.

**Sektor keuangan butuh standar keamanan siber yang lebih ketat.**
Insiden BSI mendorong OJK untuk memperketat regulasi keamanan siber di sektor perbankan. POJK tentang ketahanan dan keamanan siber perbankan menjadi lebih diperkuat pasca insiden ini.

**Dwell time adalah ancaman yang sering diabaikan.**
LockBit tidak langsung mengenkripsi begitu masuk. Mereka diam-diam berada di jaringan, memetakan sistem, mencuri data, dan menunggu momen yang tepat. Deteksi dini di fase ini jauh lebih murah dari sisi dampak dibanding menunggu enkripsi sudah terjadi.

**Bank syariah bukan target yang lebih aman.**
Tidak ada "security through obscurity" di dunia ransomware. Kelompok seperti LockBit menyerang siapa saja yang punya nilai dan kemampuan membayar, tanpa memandang jenis institusinya.

---

## Key Takeaways

- Bank BSI diserang LockBit 3.0 pada Mei 2023, menyebabkan layanan perbankan lumpuh beberapa hari.
- LockBit menggunakan double extortion: enkripsi data plus ancaman publikasi data nasabah.
- 1,5 TB data diklaim dicuri termasuk data 15 juta nasabah, password, dan dokumen internal.
- BSI tidak transparan dalam komunikasi awal, menyebut serangan sebagai "gangguan teknis."
- LockBit adalah salah satu kelompok ransomware paling aktif di dunia, beroperasi dengan model RaaS.
- Insiden ini mendorong pengetatan regulasi keamanan siber perbankan oleh OJK.
- Ransomware modern bukan hanya soal enkripsi: exfiltration data sebelum enkripsi menjadikan backup saja tidak cukup.

---

## Sources

- [Teguh Aprianto: Konfirmasi Serangan BSI](https://twitter.com/secgron) - pakar keamanan siber Indonesia yang pertama mengkonfirmasi secara publik
- [Kompas: Kronologi Serangan Siber BSI](https://www.kompas.com) - timeline dan liputan kejadian
- [CNBC Indonesia: LockBit Klaim Serangan BSI](https://www.cnbcindonesia.com) - liputan klaim LockBit
- [OJK: Respons Regulasi Pasca BSI](https://www.ojk.go.id) - tindak lanjut regulasi
- Europol: LockBit Takedown Operation (Februari 2024)

---

*case-studies / breaches · Dibuat: 2026-06-04*
