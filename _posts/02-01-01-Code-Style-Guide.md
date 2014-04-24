---
title: Panduan Code Style
anchor: code_style_guide
---

# Panduan Code Style  {#code_style_guide_title}

Komunitas PHP adalah besar dan beragam, terdiri dari perpustakaan yang tak terhitung banyaknya, kerangka kerja, dan komponen. Adalah umum bagi
Pengembang PHP untuk memilih beberapa ini dan menggabungkan mereka ke dalam satu proyek. Adalah penting bahwa kode PHP mematuhi
(sedekat mungkin) dengan gaya kode umum untuk memudahkan bagi pengembang untuk mencampur dan mencocokkan berbagai perpustakaan untuk
proyek-proyek mereka.

The [Kerangka Interop Grup] [ara] telah mengusulkan dan menyetujui serangkaian rekomendasi gaya. Tidak semua dari mereka terkait
kode-gaya, tapi mereka yang melakukan [PSR-0] [psr0], [PSR-1] [PSR1], [PSR-2] [psr2] dan [PSR-4] [psr4]. rekomendasi ini
hanyalah seperangkat aturan bahwa beberapa proyek seperti Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium,
dll mulai mengadopsi. Anda dapat menggunakannya untuk proyek-proyek Anda sendiri, atau terus menggunakan gaya pribadi Anda sendiri.

Idealnya Anda harus menulis kode PHP yang mematuhi standar yang dikenal. Ini bisa berupa kombinasi dari PSR, atau satu
standar coding yang dibuat oleh PEAR atau Zend. Ini berarti pengembang lain dapat dengan mudah membaca dan bekerja dengan kode Anda,
dan aplikasi yang menerapkan komponen dapat memiliki konsistensi bahkan ketika bekerja dengan banyak kode pihak ketiga.

* [Baca tentang PSR-0][psr0]
* [Baca tentang PSR-1][psr1]
* [Baca tentang PSR-2][psr2]
* [Baca tentang PSR-4][psr4]
* [Baca tentang PEAR Coding Standards][pear-cs]
* [Baca tentang Zend Coding Standards][zend-cs]
* [Baca tentang Symfony Coding Standards][symfony-cs]

Anda dapat menggunakan [PHP_CodeSniffer] [phpcs] untuk memeriksa kode terhadap salah satu dari rekomendasi tersebut, dan plugin untuk editor teks seperti [Text Sublime 2] [st-cs] diberikan umpan balik real time.

Gunakan Fabien Potencier ini [PHP Coding Standards Fixer] [phpcsfixer] untuk secara otomatis mengubah sintaks kode Anda sehingga
sesuai dengan standar-standar ini, menghemat dari memperbaiki setiap masalah dengan tangan.

Bahasa Inggris lebih disukai untuk semua nama simbol dan infrastruktur kode. Komentar dapat ditulis dalam bahasa yang mudah dibaca
oleh semua pihak saat ini dan masa depan yang mungkin bekerja di basis kode.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[zend-cs]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[symfony-cs]: http://symfony.com/doc/current/contributing/code/standards.html
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
