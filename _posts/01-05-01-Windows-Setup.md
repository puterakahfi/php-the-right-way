---
title: Setup di Windows
isChild: true
anchor: windows_setup
---

## Setup di Windows {#windows_setup_title}

PHP tersedia dalam beberapa cara untuk Windows. Anda dapat [men-download binari] [php-download] dan sampai saat ini Anda bisa menggunakan '. Msi' installer. Installer tidak lagi didukung dan berhenti di PHP 5.3.0.

Untuk pengembangan pembelajaran dan lokal Anda dapat menggunakan built in webserver dengan PHP 5.4 + sehingga Anda tidak perlu khawatir tentang konfigurasi itu. Jika Anda
ingin "all-in-one" yang mencakup webserver full-blown dan MySQL juga kemudian alat-alat seperti [Web Platform Installer] [WPI],
[Zend Server CE] [zsce], [XAMPP] [xampp] dan [WAMP] [wamp] akan membantu mendapatkan lingkungan Windows pembangunan dan berjalan cepat. Yang mengatakan, alat ini akan
sedikit berbeda dari produksi jadi hati-hati perbedaan lingkungan jika Anda bekerja pada Windows dan menggunakan untuk Linux.


Jika Anda perlu untuk menjalankan sistem produksi pada Windows maka IIS7 akan memberikan yang paling stabil dan kinerja terbaik. Anda dapat menggunakan
[phpmanager] [phpmanager] (plugin GUI untuk IIS7) untuk membuat konfigurasi dan mengelola PHP sederhana. IIS7 dilengkapi dengan FastCGI dibangun dan siap
untuk pergi, Anda hanya perlu mengkonfigurasi PHP sebagai handler. Untuk dukungan dan sumber daya tambahan ada [daerah khusus pada iis.net] [php-iis] untuk
PHP.

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/en/products/server-ce/
[xampp]: http://www.apachefriends.org/en/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
