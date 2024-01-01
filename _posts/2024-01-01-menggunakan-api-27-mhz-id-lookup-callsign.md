---
layout: post
title: "Cara Menggunakan API 27mhz.id untuk Melakukan Lookup Nama Pemilik 10-28"
date: 2024-01-01 12:00:00 +0700
categories: google javascript appscript api
---

Jika Anda ingin melakukan lookup nama pemilik dalam format 10-28 menggunakan API 27mhz.id di Excel atau Google Sheets, berikut adalah langkah-langkahnya:

**Langkah 1: Persiapkan Data**

Pastikan Anda memiliki data 10-28 yang akan Anda cari nama pemiliknya. Misalnya, letakkan data ini di sel B1 dalam format JZxxyyy, seperti contoh JZ09AQC, JZ36OKE, dan sebagainya.

**Langkah 2: Masukkan Formula**

Kemudian, masukkan formula berikut di sel C1 atau sel mana pun yang sesuai dengan kebutuhan Anda:

```excel
=IMPORTDATA("https://api.27mhz.id/getname&cs="&B1)
```

**Langkah 3: Menghilangkan N/A yang Mengganggu**

Untuk menghindari tampilan N/A yang mengganggu jika sel B1 kosong, Anda dapat menggunakan rumus berikut:

```excel
=IF(B1="","",IMPORTDATA("https://api.27mhz.id/getname&cs="&B1))
```

Dengan menggunakan rumus ini, jika sel B1 kosong, maka sel C1 juga akan tetap kosong tanpa menampilkan N/A.

**Langkah 4: Hasil Lookup Nama**

Hasil dari lookup nama pemilik 10-28 akan muncul di sel C1 atau di tempat yang Anda tentukan sesuai dengan rumus yang Anda gunakan.

Semoga panduan ini bermanfaat untuk Anda dalam melakukan lookup nama pemilik menggunakan API 27mhz.id di Excel atau Google Sheets.

---
