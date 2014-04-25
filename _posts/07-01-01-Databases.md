---
title: Databases
anchor: databases
---

# Databases {#databases_title}

Banyak kali kode PHP Anda akan menggunakan database untuk bertahan informasi . Anda memiliki beberapa pilihan untuk menghubungkan dan berinteraksi
dengan database Anda . Pilihan yang dianjurkan _until PHP 5.1.0_ adalah menggunakan driver asli seperti [ mysql ] [ mysql ] , [ mysqli ] [ mysqli ] , [ pgsql ] [ pgsql ] , dll

Driver asli yang besar jika Anda hanya menggunakan SATU database dalam aplikasi Anda , tetapi jika , misalnya , Anda menggunakan MySQL dan sedikit MSSQL ,
atau Anda perlu menghubungkan ke database Oracle , maka Anda tidak akan dapat menggunakan driver yang sama . Anda akan perlu belajar API baru untuk masing-masing
Database - dan yang bisa konyol .

Sebagai catatan tambahan pada driver asli , ekstensi mysql untuk PHP tidak lagi aktif dalam pembangunan , dan secara resmi ditinggalkan pada PHP 5.5 , yang berarti bahwa itu akan dihapus dalam beberapa rilis berikutnya . Jika Anda menggunakan ` mysql_connect ( ) ` dan ` mysql_query ( ) ` dalam aplikasi Anda maka Anda akan dihadapkan dengan penulisan ulang di beberapa titik bawah
line, sehingga pilihan terbaik adalah untuk menggantikan penggunaan mysql dengan mysqli atau PDO dalam aplikasi Anda dalam jadwal pembangunan Anda sendiri sehingga Anda tidak akan
terburu-buru nanti . _If Anda memulai dari awal maka benar-benar tidak menggunakan ekstensi mysql : menggunakan [ MySQLi extension ] [ mysqli ] , atau menggunakan PDO._

* [PHP: Choosing an API for MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)

## PDO

PDO adalah database perpustakaan koneksi abstraksi - dibangun ke PHP 5.1.0 sejak - yang menyediakan antarmuka umum untuk berbicara dengan
banyak database yang berbeda. PDO tidak akan menerjemahkan query SQL atau meniru fitur yang hilang; itu adalah murni untuk menghubungkan ke beberapa jenis
database dengan API yang sama.

Lebih penting lagi, `` PDO memungkinkan Anda untuk dengan aman menyuntikkan masukan asing (misalnya ID) ke dalam query SQL Anda tanpa khawatir tentang database serangan injeksi SQL.
Ini dimungkinkan dengan pernyataan PDO dan parameter terikat.

Mari kita asumsikan script PHP menerima ID numerik sebagai parameter permintaan. ID ini harus digunakan untuk mengambil catatan pengguna dari database. Ini adalah `salah`
cara untuk melakukan ini:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NO!
{% endhighlight %}

Ini adalah kode yang mengerikan. Anda memasukkan parameter permintaan mentah menjadi query SQL. Ini akan membuat Anda hack dalam
detak jantung. Bayangkan saja jika seorang hacker lewat di parameter inventif `id` dengan memanggil URL seperti
`http://domain.com/?id=1% 3BDELETE + FROM pengguna +`. Ini akan mengatur `$ _GET ['id']` variabel `1; DELETE FROM pengguna`
yang akan menghapus semua pengguna Anda! Sebaliknya, Anda harus membersihkan ID input menggunakan PDO terikat parameter.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); // <-- Automatically sanitized by PDO
$stmt->execute();
{% endhighlight %}

Ini adalah kode yang benar. Ini menggunakan parameter terikat pada pernyataan PDO. Ini lolos ID masukan asing sebelum diperkenalkan ke
Database mencegah serangan injeksi SQL potensial.

* [Pelajari tentang PDO][1]

Anda juga harus menyadari bahwa koneksi database menggunakan sumber daya dan itu tidak pernah terdengar-dari memiliki sumber daya
habis jika koneksi tidak secara implisit ditutup, namun ini lebih umum dalam bahasa lain. Menggunakan PDO Anda
implisit dapat menutup koneksi dengan menghancurkan objek dengan memastikan semua referensi yang tersisa untuk itu akan dihapus,
yaitu diatur ke NULL. Jika Anda tidak melakukan ini secara eksplisit, PHP secara otomatis akan menutup koneksi ketika naskah Anda berakhir -
kecuali tentu saja Anda menggunakan koneksi persistent.

* [Pelajari tentang PDO connections][5]

## Abstraction Layers

Banyak kerangka menyediakan lapisan abstraksi mereka sendiri yang mungkin atau mungkin tidak duduk di atas PDO. Ini akan sering meniru fitur untuk
satu sistem database yang lain hilang dari yang lain dengan membungkus pertanyaan Anda dalam metode PHP, memberikan Anda abstraksi database sebenarnya.
Hal ini tentu saja akan menambah biaya overhead sedikit, tetapi jika Anda sedang membangun sebuah aplikasi portable yang perlu untuk bekerja dengan MySQL, PostgreSQL dan
SQLite maka overhead kecil akan sia-sia demi kode kebersihan.

Beberapa lapisan abstraksi telah dibangun menggunakan [PSR-0] [psr0] atau [PSR-4] [psr4] standar namespace sehingga dapat diinstal dalam aplikasi apapun yang Anda suka:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Propel][7]
* [ZF2 Db][4]
* [ZF1 Db][3]

[1]: http://www.php.net/manual/en/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[3]: http://framework.zend.com/manual/en/zend.db.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[5]: http://php.net/manual/en/pdo.connections.php
[6]: https://github.com/auraphp/Aura.Sql
[7]: http://propelorm.org/Propel/

[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
