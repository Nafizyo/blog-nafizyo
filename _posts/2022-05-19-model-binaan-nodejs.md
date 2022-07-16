---
layout: post
title: "Model Binaan Node.js"
date: 2022-05-19
---

Node.js adalah sebuah runtime Javascript, binaannya bermodelkan sifat berasing masa dan berpacukan kejadian. Dalam [dokumentasi rasmi Node.js](https://nodejs.org/), [pengenalan Node.js](https://nodejs.org/en/about/) itu sendiri bermula dengan: "*As an **asynchronous event-driven JavaScript runtime**, Node.js is designed to build scalable network applications.*"

Model Binaan Node.js
====================

Pembangunan web zaman milenium berkehendak kepada teknologi yang mempunyai [keserentakan](https://ms.wikipedia.org/wiki/Keserentakan_(sains_komputer)) yang lebih baik berbanding pelayan-pelayan web popular pada tahun 1990-an seperti PHP - Apache. Maka, kedua-dua sifat Node.js di atas menjadi ciri utama yang melayakkannya untuk menjadi jawapan kepada kehendak ini, malah memang pun Node.js dicipta untuk tujuan tersebut. Mari fahami lebih lanjut tentang kedua-duanya.

*Baca rencana tentang bandingan tahap keserentakan Node.js dengan Apache - [Nodejs vs Apache: Performance Battle For The Conquest Of My Heart](https://dev.to/emiliosp/nodejs-vs-apache-performance-battle-for-the-conquest-of-my-5c4n).*

*Baca rencana tentang bandingan ciri-ciri Node.js dengan PHP - [PHP vs. Node.js - GeeksforGeeks](https://www.geeksforgeeks.org/php-vs-node-js/#:~:text=PHP%20scripts%20have%20an%20extension,Chrome's%20JavaScript%20Engine(V8)).*

Node.js dan Asynchronous: Pengenalan Keberasingan Masa
------------------------------------------------------

Sifat asynchronous (yang saya sebut berasing masa) membenarkan Node.js mengendalikan kerja secara *non-blocking*. Andaikan seorang pelayan kedai makan yang mengambil pesanan dari 2 meja yang berbeza: yang pertama memesan nasi goreng dan yang kedua memesan air kosong. Air kosong siap dahulu jadi pesanan kedua dihidangkan dulu walaupun pesanan pertama datang lebih awal. 

Asynchronous berlawanan dengan synchronous (saya sebut berturut masa) yang mengendalikan kerja secara *blocking*. Andaikan pelayan yang sama tadi dalam situasi yang sama, tetapi kali ini walaupun air kosong sudah siap tetapi pesanan pertama iaitu nasi goreng ditunggu dan dihantar olehnya terlebih dahulu.

*Baca rencana ringkas yang menerangkan konsep ini secara mudah difahami - [What is Asynchronous - Definition from Techopedia](https://www.techopedia.com/definition/17757/asyncronous).*

*Baca rajutan bergrafik tentang perbandingan asynchronous dengan syncronous - [Synchronous and Asynchronous Programming](https://twitter.com/Rapid_API/status/1527636774037639168?s=20&t=1DFr9gc_CwDenDr1y3b0vg).*

Node.js dan Event-Driven: Pengenalan Pacuan Kejadian
----------------------------------------------------

Memetik dokumentasi, kebanyakan API teras Node dibina berpaksikan *"event-driven architecture in which certain kinds of objects (called "emitters") emit named events that cause Function objects ("listeners") to be called"*.

Nampaknya 2 objek terlibat di sini, 1: penyiar, dan 2: pendengar. Gambaran besarnya di sini, semua objek yang menyiar tergolong dalam kelas eventEmitter. Penyiar menyiarkan kejadian yang berlaku, lalu pendengar bertindak balas. Itu sahaja.

Untuk lebih daripada itu, yang pertama patut diketahui ialah ada 2 jenis kejadian, 1: kejadian asal, dan 2: kejadian buatan. Tetapi hanya kejadian buatan perlu disiarkan sendiri oleh pengatur. Ini dilaksanakan dengan fungsi eventEmitter.emit().

Untuk membenarkan pengatur sendiri menetapkan hubungan antara kejadian dengan tindak balas, penyiar mendedahkan fungsi eventEmitter.on(). Patut diketahui yang bagi setiap kejadian, 1 atau lebih tindak balas boleh ditetapkan. Jika berbilang, tindak balas akan berjalan secara berturut masa supaya tiada race condition & ralat logik.

Inilah yang dinamakan bermodelkan sifat berpacukan kejadian, dengan kata lain berseni binakan pacuan kejadian, atau juga di sesetengah tempat namanya dipacu kejadian. Dan inilah antara ciri unggul Node.js yang membenarkannya bekerja secara berasing masa.

*Baca panduan modul Events di dokumentasi Node - [Events : Node.js v16.15.0 Documentation](https://nodejs.org/dist/latest-v16.x/docs/api/events.html#events).*



