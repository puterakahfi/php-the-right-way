---
isChild: true
anchor: namespaces
---

## Namespaces {#namespaces_title}

Sebagaimana disebutkan di atas, komunitas PHP memiliki banyak pengembang menciptakan banyak kode. Ini berarti bahwa
kode PHP satu perpustakaan dapat menggunakan nama kelas yang sama dengan perpustakaan lain. Ketika kedua perpustakaan digunakan
dalam namespace yang sama, mereka bertabrakan dan menyebabkan masalah.


_Namespaces_ Memecahkan masalah ini. Seperti dijelaskan dalam manual referensi PHP, ruang nama dapat dibandingkan
ke direktori sistem operasi yang _namespace_ file; dua file dengan nama yang sama dapat hidup berdampingan dalam
direktori terpisah. Demikian juga, dua kelas PHP dengan nama yang sama dapat hidup berdampingan dalam PHP terpisah
namespaces. Ini sesederhana itu.

Hal ini penting bagi Anda untuk namespace kode Anda sehingga dapat digunakan oleh pengembang lain tanpa rasa takut
bertabrakan dengan perpustakaan lain.

Salah satu cara yang direkomendasikan untuk menggunakan namespaces diuraikan dalam [PSR-0] [psr0], yang bertujuan untuk memberikan file standar, kelas dan namespace konvensi untuk memungkinkan kode plug-and-play.

Pada bulan Desember 2013 PHP-FIG menciptakan standar baru autoloading: [PSR-4] [psr4], yang suatu saat akan
mungkin menggantikan PSR-0. Saat ini keduanya masih digunakan, sebagai PSR-4 membutuhkan PHP 5.3 dan banyak PHP 5.2-only
proyek yang saat ini menerapkan PSR-0. Jika Anda akan menggunakan standar autoloader untuk aplikasi baru atau
Paket maka Anda hampir pasti ingin melihat ke dalam PSR-4.

* [Baca tentang Namespaces][namespaces]
* [Baca tentang PSR-0][psr0]
* [Baca tentang PSR-4][psr4]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
