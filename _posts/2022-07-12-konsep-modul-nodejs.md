Modul Node.js: Konsep, Jenis dan Contoh Modul Node.js
=====================================================

Modul ialah anggota, dengan maksud bahagian tersendiri yang ada peranan tersendiri. Ia sama seperti anggota dalaman dan luaran badan yang masing-masing ada tugasnya. Semua anggota ini terhubung satu sama lain dengan sambungan tertentu lalu membenarkan kerjasama sebagai satu badan berlaku.

Dalam dunia pengaturcaraan dan di luarnya, konsep rekaan bermodul atau modular mempunyai penerapan yang sudah meluas. Sebagai contoh, jika anda pengguna PC, sangat mungkin yang papan kekunci dan tetikus anda kedua-duanya bukanlah bersekali dengan bahagian komputer yang lain, sebaliknya adalah bahagian yang boleh dipasang, ditanggalkan atau diganti dengan papan kekunci dan tetikus lain. Itu contoh mudah untuk rekaan bermodul.

Jenis Modul Node.js
-------------------

Jenis pertama dipanggil **modul teras**. Teras bermaksud API teras yang membentuk komponen utama Node.js bersama enjin V8 yang dibincangkan dalam [rencana sebelum ini](https://blog-nafizyo.netlify.app/2022/05/17/blog-nafizyo-belajar-nodejs-sebuah-permulaan.html). Komponen utama yang dimaksudkan antara lainnya API pelayan HTTP, sarana-sarana pengurusan fail, OS, URL, DNS, sarana pacuan kejadian dan sebagainya.

Jenis kedua dipanggil **modul setempat**. Setempat di sini bermaksud buatan setempat, jadi jika pengatur menulis satu atau beberapa fungsi dalam berkas berasingan dengan berkas utama aplikasi Nodenya, ia dipanggil sebagai modul setempat.

Jenis ketiga dipanggil **modul pihak ketiga**. Sesuai dengan namanya, ia ditulis oleh pihak ketiga iaitu pengatur lain lalu dimuat naik ke laman pengurus pakej seperti npm dan yarn. Sesiapa sahaja boleh memuat turun dan menggunakan modul-modul ini secara percuma.

Kebanyakan bentuk aplikasi Node menuntut pengatur untuk menggunakan kesemua 3 jenis modul di atas. Hal ini demikian kerana masing-masing jenis memiliki kelebihan yang tersendiri yang selalunya diperlukan secara bersama untuk menyempurnakan sesebuah aplikasi Node.

Konsep Modul Node.js
--------------------

Andaikan ada sebuah aplikasi Node untuk sistem markah peperiksaan. Di dalamnya, ada berkas app.js yang mengandungi pelayan web, dan ada berkas db.js yang mengandungi pintu ke pangkalan data. Itu sahaja. Lalu, seorang pengguna melawat sistem ini dan mencari suatu data peperiksaan, tetapi pelayan tidak dapat mengembalikan apa-apa hasil. 

Mengapa?

Apa yang berlaku adalah: oleh sebab Node.js bersifat modular, si pelayan yang tinggal di app.js tidak dapat mencapai pintu yang berada di db.js. Untuk menyelesaikan masalah ini, satu laluan perlu dibina antara dua berkas tersebut.

Di sinilah peranan `export` dan `import`: yang satu untuk db.js mendedahkan fungsi di dalamnya kepada semua berkas lain, dan yang satu lagi untuk berkas lain mendapatkan fungsi yang sudah terdedah tadi.

Masalah selesai~

Masalah Modul dalam Javascript: Pengenalan Sistem Modul CommonJS dan ECMAScript
-------------------------------------------------------------------------------

Modul ialah anggota. Setiap anggota ada tugasnya; mereka terhubung satu sama lain untuk membenarkan kerjasama sebagai satu badan berlaku. 

Jika modul ialah anggota, maka pengaturcaraan modular ibarat penciptaan sebuah badan: ia merupakan seni menggubah banyak anggota menjadi satu badan. Dan seperti seni-seni yang lain, semakin bebas ia daripada peraturan, semakin beragam pula persembahan karya-karyanya. Hal seumpama ini adalah masalah bagi sebuah bidang teknikal, dan inilah masalah pengaturcaraan Javascript sejak tahun 1995 hingga 2015: ketiadaan peraturan yang piawai tentang tatacara export dan import modul.

Penyelesaian kepada masalah ini adalah sesuatu yang dipanggil **sistem modul**, dan ia bukan tidak pernah diusulkan. Sistem modul AMD, UMD dan CommonJS adalah antara sistem modul yang wujud ketika itu, tetapi tiada satu pun yang dianggap benar-benar mengatasi yang lain.

Pada tahun 2015, akhirnya Pertubuhan Pengeluar Komputer Eropah (Ecma International atau ECMA) sebagai penggubal piawaian TMK Eropah telah mengeluarkan sebuah sistem modul bernama ECMAScript modules (atau ES modules). 

Maka, masalah pun selesai~

Node.js lain sedikit: sejak diperkenalkan pada 2009 lagi ia menggunakan sistem CommonJS, dan terus menyokong CJS hingga sekarang sambil menambah sokongan terhadap ECMAScript. Dalam satu perkembangan, pada Mei 2020, Node.js v12.17.0 

*Baca lebih lanjut tentang perbezaan CommonJS dengan ECMAScript dalam rencana ini - [CommonJS vs ES modules in Node.js](https://blog.logrocket.com/commonjs-vs-es-modules-node-js/#:~:text=ES%20modules%20are%20the%20standard,encapsulating%20JavaScript%20code%20for%20reuse)*

Perbezaan Export dan Import antara Modul Teras, Setempat dan Pihak Ketiga
-------------------------------------------------------------------------

Walaupun memakai konsep modular yang sama, tetapi peraturan export dan import sedikit berbeza antara tiga jenis modul ini. 

Bagi modul teras, Node.js memuatkan dan mendedahkan semuanya semasa program bermula. Modul-modul ini ditakrifkan dalam kod sumber Node.js dan terletak dalam sampul /lib. Oleh itu, tiada keperluan untuk export modul teras, hanya import. Malah, modul teras sentiasa akan mengatasi modul pihak ketiga yang mempunyai nama sama dengannya apabila diimport.

Bagi modul setempat, pengatur perlu mengisi objek `module.exports` dengan fungsi yang ingin dieksport. Perintah ini boleh ditulis sebaik sahaja selepas fungsi tersebut atau di bahagian paling bawah dalam berkas. Patut diketahui yang module ialah pemboleh ubah yang merujuk kepada modul semasa (yakni fail semasa), manakala exports ialah objek yang ingin dieksport. `module.exports` ialah objek istimewa yang datang bersama setiap fail dalam aplikasi Node.js, tugasnya adalah mendedahkan setiap fungsi yang diisi ke dalamnya.

Bagi modul pihak ketiga, Node.js menyimpan semuanya dalam sampul **node_modules** di root folder. Selain itu, berkas package.json di root folder menyimpan nama-nama modul dalam node_modules sebagai dependencies. Selebihnya, seperti modul teras, tiada keperluan untuk export modul pihak ketiga, hanya import.

Penutup
-------



