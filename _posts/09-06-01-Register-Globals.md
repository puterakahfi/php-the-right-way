---
isChild: true
anchor: register_globals
---

## Register Globals {#register_globals_title}

** CATATAN: ** Pada PHP 5.4.0 yang `register_globals` pengaturan telah dihapus dan tak dapat
lagi digunakan. Ini hanya disertakan sebagai peringatan bagi siapa pun dalam proses upgrade aplikasi warisan.

Bila diaktifkan, `register_globals` pengaturan konfigurasi yang membuat beberapa jenis variabel (termasuk yang dari
`$ _POST`, `$ _GET` Dan `$ _REQUEST`) tersedia dalam lingkup global aplikasi Anda. Hal ini dapat dengan mudah menyebabkan
masalah keamanan sebagai aplikasi Anda tidak dapat secara efektif mengatakan di mana data berasal.

Sebagai contoh: `$ _GET ['foo']` akan tersedia melalui `$ foo`, yang dapat menimpa variabel yang belum dideklarasikan.
Jika Anda menggunakan PHP <5.4.0 __ membuat sure__ bahwa `register_globals` adalah __ off__.

* [Register_globals di PHP manual](http://www.php.net/manual/en/security.globals.php)
