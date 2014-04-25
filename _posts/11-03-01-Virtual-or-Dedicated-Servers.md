---
title: Virtual atau Dedicated Servers
isChild: true
anchor: virtual_or_dedicated_servers
---

## Virtual atau Dedicated Servers {#virtual_or_dedicated_servers_title}

Jika Anda merasa nyaman dengan sistem administrasi, atau tertarik untuk belajar itu, server virtual atau dedicated memberikan kontrol penuh terhadap lingkungan produksi aplikasi Anda.

### nginx dan PHP-FPM

PHP, PHP melalui built-in FastCGI Process Manager (FPM), pasangan benar-benar baik dengan [nginx] (http://nginx.org), yang merupakan ringan, kinerja tinggi server web. Ini menggunakan memori kurang dari Apache dan lebih baik dapat menangani permintaan lebih bersamaan. Hal ini sangat penting pada server virtual yang tidak memiliki banyak memori untuk cadangan.

* [Baca lebih lanjut tentang nginx](http://nginx.org)
* [Baca lebih lanjut tentang PHP-FPM](http://php.net/manual/en/install.fpm.php)
* [Baca lebih lanjut tentang setting nginx dan PHP-FPM dengan aman](https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/)

### Apache dan PHP

PHP dan Apache memiliki sejarah panjang bersama-sama . Apache adalah liar dikonfigurasi dan memiliki banyak tersedia [ modul ] ( http://httpd.apache.org/docs/2.4/mod/ ) untuk memperluas fungsi . Ini adalah pilihan populer untuk server bersama dan setup yang mudah untuk kerangka kerja PHP dan aplikasi open source seperti WordPress . Sayangnya , Apache menggunakan sumber daya lebih dari nginx secara default dan tidak dapat menangani banyak pengunjung pada saat yang sama .

Apache memiliki beberapa konfigurasi yang mungkin untuk menjalankan PHP . Yang paling umum dan paling mudah untuk setup adalah [ prefork MPM ] ( http://httpd.apache.org/docs/2.4/mod/prefork.html ) dengan mod_php5 . Meskipun bukan yang paling efisien memori , itu adalah yang paling sederhana untuk mendapatkan kerja dan digunakan. Ini mungkin adalah pilihan terbaik jika Anda tidak ingin menggali terlalu dalam ke aspek administrasi server . Catatan bahwa jika Anda menggunakan mod_php5 Anda harus menggunakan prefork MPM .

Atau, jika Anda ingin memeras lebih banyak kinerja dan stabilitas dari Apache maka Anda dapat mengambil keuntungan dari sistem FPM sama seperti nginx dan menjalankan [ pekerja MPM ] ( http://httpd.apache.org/docs/2.4/mod/ worker.html ) atau [ event MPM ] ( http://httpd.apache.org/docs/2.4/mod/event.html ) dengan mod_fastcgi atau mod_fcgid . Konfigurasi ini akan secara signifikan lebih banyak memori efisien dan jauh lebih cepat tetapi lebih banyak pekerjaan untuk mengatur .

* [Baca lebih lanjut tentang Apache](http://httpd.apache.org/)
* [Baca lebih lanjut tentang Multi-Processing Modules](http://httpd.apache.org/docs/2.4/mod/mpm_common.html)
* [Baca lebih lanjut tentang mod_fastcgi](http://www.fastcgi.com/mod_fastcgi/docs/mod_fastcgi.html)
* [Baca lebih lanjut tentang mod_fcgid](http://httpd.apache.org/mod_fcgid/)
