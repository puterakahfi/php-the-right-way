---
title: Composer dan Packagist
isChild: true
anchor: composer_and_packagist
---

## Composer dan Packagist {#composer_and_packagist_title}

Komposer adalah brilian ketergantungan manajer ** ** untuk PHP. Daftar dependensi proyek Anda dalam file `composer.json` dan, dengan beberapa perintah sederhana, Komposer secara otomatis akan mendownload dependensi proyek Anda dan setup autoloading untuk Anda.

Sudah ada banyak PHP perpustakaan yang kompatibel dengan Composer, siap untuk digunakan dalam proyek Anda. Ini "paket" yang tercantum pada [Packagist] [1], repositori resmi untuk Komposer-kompatibel PHP perpustakaan.

### Cara Install Composer

Anda dapat menginstal Composer lokal (dalam direktori kerja Anda saat ini, meskipun hal ini tidak lagi dianjurkan) atau global (misalnya / usr / local / bin). Mari kita berasumsi bahwa Anda ingin menginstal Composer lokal. Dari direktori root proyek Anda:

    curl -s https://getcomposer.org/installer | php

Ini akan men-download `composer.phar` (arsip biner PHP). Anda dapat menjalankan ini dengan `php` untuk mengelola dependensi proyek Anda. <strong> Harap Catatan: </ strong> Jika Anda pipa download kode langsung ke penerjemah, silakan baca kode online untuk mengkonfirmasi aman.

#### Install di Windows

Untuk pengguna Windows cara termudah untuk bangun dan berjalan adalah dengan menggunakan [ComposerSetup] [6] installer, yang melakukan instalasi global dan set up Anda `$ PATH` sehingga Anda hanya dapat memanggil `komposer` dari direktori manapun dalam Anda baris perintah.

### Cara Install Composer (manual)

Manual menginstal Composer adalah teknik canggih; Namun, ada berbagai alasan mengapa pengembang mungkin lebih memilih metode ini vs menggunakan rutin instalasi interaktif. Instalasi interaktif memeriksa instalasi PHP Anda untuk memastikan bahwa:

- versi PHP yang cukup sedang digunakan
- `Phar` file. dapat dijalankan dengan benar
- hak akses direktori tertentu yang cukup
- ekstensi bermasalah tertentu tidak dimuat
- tertentu `php.ini` pengaturan ditetapkan

Karena instalasi manual tidak ada pemeriksaan ini melakukan, Anda harus memutuskan apakah trade-off sangat berharga untuk Anda. Dengan demikian, di bawah ini adalah bagaimana untuk mendapatkan Komposer secara manual:

    curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

Jalan `$ HOME / local / bin` (atau direktori pilihan Anda) harus di `$ PATH` variabel lingkungan Anda. Hal ini akan mengakibatkan seorang komposer `perintah` yang tersedia.

Bila Anda menemukan dokumentasi yang menyatakan untuk menjalankan Komposer sebagai `php` composer.phar install, Anda dapat mengganti bahwa dengan:

    composer install
    
Bagian ini akan menganggap Anda telah menginstal komposer global.

### Cara mendefinisakan ketergantungan dan cara installnya

Komposer melacak dependensi proyek Anda dalam sebuah file yang bernama `composer.json`. Anda dapat mengelolanya dengan tangan jika Anda suka, atau penggunaan Composer sendiri. The `komposer memerlukan` perintah menambahkan ketergantungan proyek dan jika Anda tidak memiliki file `composer.json`, salah satu akan dibuat. Berikut ini adalah contoh yang menambahkan [Ranting] [2] sebagai ketergantungan proyek Anda.

	composer require twig/twig:~1.8

Atau yang `perintah` komposer init akan memandu Anda melalui penciptaan file penuh `composer.json` untuk proyek Anda. Either way, setelah Anda membuat file `composer.json` Anda, Anda dapat memberitahu Composer untuk men-download dan menginstal dependensi Anda ke `vendor /` direktori. Hal ini juga berlaku untuk proyek-proyek yang telah anda download yang sudah menyediakan file `composer.json`:

    composer install

Selanjutnya, tambahkan baris ini ke file PHP utama aplikasi Anda; ini akan memberitahu PHP untuk menggunakan autoloader Composer untuk dependensi proyek Anda.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Sekarang Anda dapat menggunakan dependensi proyek Anda, dan mereka akan otomatis diambil pada permintaan.

### Meng-update ketergantungan

Komposer menciptakan sebuah file bernama `composer.lock` yang menyimpan versi yang tepat dari setiap paket yang di-download ketika Anda pertama kali menjalankan `php composer.phar install`. Jika Anda berbagi proyek Anda dengan coders lain dan file `composer.lock` merupakan bagian dari distribusi Anda, ketika mereka menjalankan `php` composer.phar menginstal mereka akan mendapatkan versi yang sama seperti Anda. Untuk memperbarui dependensi, jalankan `update` php composer.phar.

Ini sangat berguna ketika Anda mendefinisikan persyaratan versi fleksibel. Misalnya persyaratan versi ~ 1,8 berarti "sesuatu yang lebih baru dari 1.8.0, tetapi kurang dari 2.0.x-dev". Anda juga dapat menggunakan `*` wildcard seperti dalam `1.8. *`. Sekarang pembaruan php composer.phar `perintah` s Composer akan meng-upgrade semua dependensi Anda ke versi terbaru yang sesuai dengan batasan yang Anda tetapkan.

### Notifikasi Update

Untuk menerima pemberitahuan tentang rilis versi baru Anda dapat mendaftar untuk [VersionEye] [3], sebuah layanan web yang dapat memonitor
GitHub dan BitBucket menyumbang `composer.json` file dan mengirim email dengan rilis paket baru.

### Cek ketergantungan Anda terhadap masalah keamanan

The [Security Advisories Checker] [4] adalah layanan web dan alat baris perintah, keduanya akan memeriksa file Anda `composer.lock` dan memberitahu Anda jika Anda perlu memperbarui dependensi Anda.

* [Pelajari Composer][5]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: https://www.versioneye.com/
[4]: https://security.sensiolabs.org/
[5]: http://getcomposer.org/doc/00-intro.md
[6]: https://getcomposer.org/Composer-Setup.exe

