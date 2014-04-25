---
isChild: true
anchor: error_reporting
---

## Error Reporting {#error_reporting_title}

Error logging dapat berguna dalam menemukan titik masalah dalam aplikasi Anda, tetapi juga dapat mengekspos informasi tentang
struktur aplikasi Anda ke dunia luar. Untuk secara efektif melindungi aplikasi Anda dari masalah yang bisa
disebabkan oleh output dari pesan-pesan ini, Anda perlu mengkonfigurasi server Anda berbeda dalam pembangunan dibandingkan
produksi (hidup).

### Development

Untuk menampilkan setiap kesalahan yang mungkin selama pengembangan </ strong>, mengkonfigurasi pengaturan berikut dalam `php.ini`:

    display_errors = On
    display_startup_errors = On
    error_reporting = -1
    log_errors = On

> Passing in the value `-1` will show every possible error, even when new levels and constants are added in future PHP versions. The `E_ALL` constant also behaves this way as of PHP 5.4. - [php.net](http://php.net/manual/function.error-reporting.php)

Tingkat `E_STRICT` error konstan diperkenalkan pada 5.3.0 dan tidak
bagian dari `E_ALL`, namun menjadi bagian dari `E_ALL` dalam 5.4.0. Apa artinya ini?
Dalam hal pelaporan setiap kesalahan yang mungkin di versi 5.3 itu berarti Anda harus
menggunakan salah `-1` atau `E_ALL | E_STRICT`.

** Pelaporan setiap kemungkinan kesalahan dengan versi PHP **

* &lt; 5.3 `-1` or `E_ALL`
* &nbsp; 5.3 `-1` or `E_ALL | E_STRICT`
* &gt; 5.3 `-1` or `E_ALL`

### Production

Untuk menyembunyikan kesalahan pada produksi <strong> Anda </ strong> lingkungan, mengkonfigurasi `php.ini` sebagai:

    display_errors = Off
    display_startup_errors = Off
    error_reporting = E_ALL
    log_errors = On

Dengan pengaturan ini dalam produksi, kesalahan masih akan login ke error log untuk server web, tetapi tidak akan
ditampilkan kepada pengguna. Untuk informasi lebih lanjut tentang pengaturan ini, lihat manual PHP:

* [error_reporting](http://php.net/manual/errorfunc.configuration.php#ini.error-reporting)
* [display_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-errors)
* [display_startup_errors](http://php.net/manual/errorfunc.configuration.php#ini.display-startup-errors)
* [log_errors](http://php.net/manual/errorfunc.configuration.php#ini.log-errors)
