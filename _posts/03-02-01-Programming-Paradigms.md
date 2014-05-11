---
title: Paradigma Pemrograman
isChild: true
anchor: programming_paradigms
---

## Paradigma Pemrograman {#programming_paradigms_title}

PHP adalah bahasa pemrograman fleksibel, dinamis, dan mendukung berbagai teknik pemrograman. Perkembangan yang sangat pesat telah terjadi di PHP selama bertahun-tahun, terutama dukungan terhadap pemrograman berorientasi objek (OOP) di PHP 5.0 (2004), _anonymous function_ dan _namespace_ di PHP 5.3 (2009), dan _trait_ di PHP 5.4 (2012).

### Pemrograman Berorientasi Object

PHP sangat mendukung pemrograman berorientasi obyek termasuk dukungan untuk _class_, _abstract class_, _interface_, _inheritance_, _constructor_, _cloning_, _exception_, dan banyak lagi.

* [Baca tentang Pemrograman Berorientasi Object pada PHP][oop]
* [Baca tentang Traits][traits]

### Pemrograman Fungsional

PHP mendukung _first class function_, yang berarti bahwa fungsi dapat dimasukkan ke dalam sebuah variabel. Kedua user-defined dan built-in fungsi dapat direferensikan oleh variabel dan dipanggil secara dinamis. Fungsi dapat disahkan sebagai argumen untuk lainnya
fungsi (fitur yang disebut fungsi-order yang lebih tinggi) dan fungsi dapat kembali fungsi lainnya.

Rekursi, sebuah fitur yang memungkinkan fungsi untuk menyebut dirinya didukung oleh bahasa, tetapi sebagian besar fokus kode PHP pada iterasi.

Fungsi anonim baru (dengan dukungan untuk penutupan) yang hadir sejak PHP 5.3 (2009).

PHP 5.4 menambahkan kemampuan untuk mengikat penutupan untuk lingkup obyek dan juga meningkatkan dukungan untuk callables sehingga mereka dapat digunakan secara bergantian dengan fungsi anonim di hampir semua kasus.

* Lanjutkan membaca [Pemrograman Fungsional pada PHP](/pages/Functional-Programming.html)
* [Baca tentang Anonymous Functions][anonymous-functions]
* [Baca tentang the Closure class][closure-class]
* [Baca lebih lanjut di the Closures RFC][closures-rfc]
* [Baca tentang Callables][callables]
* [Baca tentang dynamically invoking functions dengan `call_user_func_array`][call-user-func-array]

### Pemrograman Meta

PHP mendukung berbagai bentuk meta-pemrograman melalui mekanisme seperti API Refleksi dan Metode Sihir. ada
Metode Sihir banyak tersedia seperti `__get ()`, `__set ()`, `__clone ()`, `__toString ()`, `__invoke ()`, dll yang memungkinkan pengembang untuk menghubungkan ke perilaku kelas. Pengembang Ruby sering mengatakan bahwa PHP kurang `method_missing`, tetapi tersedia sebagai `__call ()` dan `__callStatic ()`.

* [Baca tentang Magic Methods][magic-methods]
* [Baca tentang Reflection][reflection]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[overloading]: http://php.net/manual/en/language.oop5.overloading.php
[oop]: http://www.php.net/manual/en/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/en/functions.anonymous.php
[closure-class]: http://php.net/manual/en/class.closure.php
[callables]: http://php.net/manual/en/language.types.callable.php
[magic-methods]: http://php.net/manual/en/language.oop5.magic.php
[reflection]: http://www.php.net/manual/en/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/en/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
