---
title: Panduan Code Style
anchor: code_style_guide
---

# Panduan Code Style  {#code_style_guide_title}

Komunitas PHP sangatlah besar dan beragam. Ada banyak _library_, _framework_, dan _component_ yang sudah tersedia.
Dalam memilih _library_-_library_ dan _framework_ ini dan menggunakannya dalam sebuah proyek, _developer_ perlu
mematuhi aturan _code style_ yang digunakan pada _framework_ tersebut.

[The PHP Framework Interop Group] [fig] telah mengusulkan dan menyetujui serangkaian rekomendasi gaya pengkodean.
Meskipun tidak semuanya terkait dengan _code style_, tapi mereka yang merumuskan [PSR-0] [psr0], [PSR-1] [PSR1], [PSR-2] [psr2] dan [PSR-4] [psr4].

Rekomendasi ini hanyalah seperangkat aturan dan sudah diadopsi oleh beberapa proyek seperti Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium, dll.
Anda dapat memilih antara mengikuti PSR untuk proyek-proyek Anda sendiri, atau terus menggunakan gaya pribadi Anda sendiri.

Idealnya Anda harus menulis kode PHP yang mematuhi standar yang dikenal. Ini bisa berupa kombinasi dari PSR, atau satu
standar coding yang dibuat oleh PEAR atau Zend. Ini berarti _developer_ lain dapat dengan mudah membaca dan bekerja dengan kode Anda, dan aplikasi yang menerapkan komponen dapat memiliki konsistensi bahkan ketika bekerja dengan banyak kode pihak ketiga.

* [Baca tentang PSR-0][psr0]
* [Baca tentang PSR-1][psr1]
* [Baca tentang PSR-2][psr2]
* [Baca tentang PSR-4][psr4]
* [Baca tentang PEAR Coding Standards][pear-cs]
* [Baca tentang Zend Coding Standards][zend-cs]
* [Baca tentang Symfony Coding Standards][symfony-cs]

Anda dapat menggunakan [PHP_CodeSniffer] [phpcs] untuk memeriksa kode terhadap salah satu dari rekomendasi tersebut, dan plugin untuk editor teks seperti [Text Sublime 2] [st-cs] dapat memberikan _feedback_ secara real time.

Gunakan _tools_ dari Fabien Potencier ini [PHP Coding Standards Fixer] [phpcsfixer] untuk secara otomatis mengubah sintaks kode Anda sehingga sesuai dengan standar-standar ini, menghemat waktu untuk memperbaiki setiap masalah secara manual.

Bahasa Inggris lebih disukai untuk semua nama simbol dan infrastruktur kode. Komentar dapat ditulis dalam bahasa yang mudah dibaca oleh semua pihak saat ini dan masa depan yang akan mengerjakan _source code_ tersebut.

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
