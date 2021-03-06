---
layout: datague
title: "Persiapan Data: Mendapatkan Arsip Perjalanan Pribadi GO-JEK via IFTTT"
short-title: "Mendapatkan Arsip Perjalanan Pribadi GO-JEK"
meta-title: "Mendapatkan Arsip Perjalanan Pribadi GO-JEK via IFTTT"
categories: datague
tags:
- GO-JEK
- Transportation
type: post
img: /images/datague/data-gojek/front.png
published: true
related: false
---

Selain untuk arsip pribadi, gue pun mengumpulkan data GO-JEK gue untuk dianalisis lebih lanjut. Banyak hal yang bisa dianalisis dari data tersebut, *there are gigantic stories behind the data*. Di episode pertama DataGue kali ini, gue bakalan berbagi cerita bagaimana cara gue mendapatkan arsip perjalanan GO-JEK via IFTTT.

Pada awalnya, gue mengumpulkan data GO-JEK dengan cara meminta langsung ke *customer care* tiap bulannya. Sayangnya data yang disajikan masih dibungkus dalam bentuk PDF sehingga gue pun perlu bekerja ekstra untuk mengubahnya ke bentuk tabel menggunakan bantuan Tabula. Barulah pada awal bulan Juli, gue mendapatkan berita gembira bahwa GO-JEK mengirimkan arsip tiap perjalanan langsung ke surel pribadi seperti halnya yang sudah dilakukan Grab sejak dahulu kala.

## Membuat Akun IFTTT

Gue pun langsung membuka akun IFTTT sebagai jembatan penghubung surel gue ke aplikasi lainnya pasca mendapatkan kabar gembira tersebut. Akun dapat dibuat melalui laman [ifttt.com](http://ifttt.com/) atau melalui aplikasi *mobile* untuk Android maupun iOS.

## Membuat Resep

Membuat resep di IFTTT sangatlah mudah. IFTTT *stands for* "If This Then That". Ada dua pernyataan yang harus dipenuhi yaitu "This" yang berfungsi sebagai *trigger* dan "That" yang berfungsi sebagai *actor*.

- **This**: mendapatkan surel (Gmail) dari _postmaster@invoices.go-jek.com_
- **That**: kirim ke LINE Notify ([Resep 1](https://ifttt.com/applets/461009p-gmail-line)) / Kirim ke Google Spreadsheet ([Resep 2](https://ifttt.com/applets/282294p-gmail-to-sheets))

<center><img src="/images/datague/data-gojek/applets.png"></center>

Dengan *trigger* yang sama, ada dua resep yang gue bikin yaitu untuk dikirimkan ke LINE Notify dan juga dikirimkan ke Google Spreadsheet. Teks yang dikirimkan ke LINE Notify tidak termasuk HTML tag sedangkan teks yang dikirimkan ke Google Spreadsheet sudah termasuk HTML tag. Resep lain yang bisa digunakan apabila kiriman lama ingin didapatkan bisa menggunakan [resep ini](https://ifttt.com/applets/90162p-automatically-sync-gmail-emails-with-receipts-orders-invoices-to-a-google-spreadsheet).

Gue memilih LINE Notify sebagai tempat penampungan data sementara dikarenakan gue bisa mendapatkan notifikasi langsung melalui LINE dan data bisa dengan mudah didapatkan melalui "backup chat as text". Sedangkan untuk Google Spreadsheet, data sudah disajikan dalam bentuk tabular. Banyak alternatif aplikasi lainnya yang bisa digunakan seperti menggunakan Dropbox sebagai tempat penampungan data dengan format .txt. Pada akhirnya gue harus membuat *script* untuk mengubah HTML atau teks yang masih berantakan tersebut ke bentuk yang lebih terstruktur.

## *Test and Deploy*

Setelah berhasil membuat resep dengan spesifikasi yang sudah ditentukan, langkah selanjutnya adalah memastikan bahwa resep tersebut berjalan sebagaimana mestinya. IFTTT akan memberitahu apabila resep yang telah dibuat (*applets*) berjalan. 

<center><img src="/images/datague/data-gojek/applets-run.png"></center>

Perlu digarisbawahi bahwasannya *latency* surel yang didapatkan dan kemudian diteruskan ke aplikasi lainnya (LINE Notify, Google Spreadseet) biasanya berkisar antara 1-5 menit. Berikut ini adalah contoh keluaran dari LINE Notify yang gue dapatkan.

<center><img src="/images/datague/data-gojek/line-notify.png"></center>

## *Extras*

Data yang sudah didapatkan via LINE Notify maupun Google Spreadsheet masih perlu diolah lagi karena masih berbentuk teks maupun HTML yang belum terstruktur. Kode di [sini](https://github.com/rasyidstat/datague-snippets/blob/master/transportation/gojek/gojek_clean.R) dapat digunakan untuk membersihkan data ke dalam bentuk tabular yang lebih terstruktur. 

---

Sangat mudah bukan? Selain untuk mendapatkan arsip perjalanan GO-JEK, banyak hal menarik lainnya yang bisa dilakukan dengan [IFTTT](/notes/ifttt-is-awesome/). 