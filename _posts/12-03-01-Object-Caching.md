---
isChild: true
anchor: object_caching
---

## Object Caching {#object_caching_title}

Ada saat-saat itu dapat bermanfaat untuk cache objek individu dalam kode Anda , seperti dengan data yang mahal
untuk mendapatkan atau database panggilan di mana hasilnya tidak mungkin berubah . Anda dapat menggunakan software object caching untuk menahan ini
potongan data dalam memori untuk akses yang sangat cepat di kemudian hari . Jika Anda menyimpan barang-barang ini untuk menyimpan data setelah Anda mengambil
mereka , kemudian menarik mereka langsung dari cache untuk permintaan berikut , Anda bisa mendapatkan peningkatan yang signifikan dalam
kinerja serta mengurangi beban pada server database Anda .

Banyak solusi bytecode caching populer membiarkan Anda cache data kustom juga, jadi ada lebih banyak alasan untuk mengambil
keuntungan dari mereka . APCu , XCache , dan WinCache semua menyediakan API untuk menyimpan data dari kode PHP Anda ke cache memori mereka .

Objek memori sistem caching yang paling sering digunakan adalah APCu dan memcached . APCu adalah pilihan yang sangat baik untuk objek
caching , itu termasuk API sederhana untuk menambahkan data Anda sendiri ke cache memory dan sangat mudah untuk setup dan menggunakan . itu
satu batasan nyata APCu adalah bahwa hal itu terikat ke server itu diinstal pada . Memcached di sisi lain dipasang
sebagai layanan terpisah dan dapat diakses di seluruh jaringan , yang berarti bahwa Anda dapat menyimpan objek dalam data yang hyper-fast
toko di lokasi pusat dan sistem yang berbeda dapat menarik dari itu .

Perhatikan bahwa ketika menjalankan PHP sebagai ( Cepat - ) aplikasi CGI dalam server Web Anda, setiap proses PHP akan memiliki sendiri
cache, yaitu APCu data tidak dibagi antara proses kerja Anda . Dalam kasus ini , Anda mungkin ingin mempertimbangkan untuk menggunakan
memcached sebaliknya, karena tidak terikat dengan proses PHP .

Dalam konfigurasi jaringan APCu biasanya akan mengungguli memcached dalam hal kecepatan akses , tapi memcached akan dapat
untuk meningkatkan lebih cepat dan lebih lanjut . Jika Anda tidak berharap untuk memiliki beberapa server menjalankan aplikasi Anda , atau tidak perlu
fitur tambahan yang memcached penawaran maka APCu mungkin pilihan terbaik Anda untuk objek caching .

Contoh logika menggunakan APCu :

{% highlight php %}
<?php
// check if there is data saved as 'expensive_data' in cache
$data = apc_fetch('expensive_data');
if ($data === false) {
    // data is not in cache; save result of expensive call for later use
    apc_add('expensive_data', $data = get_expensive_data());
}

print_r($data);
{% endhighlight %}

Perhatikan bahwa sebelum PHP 5.5, APC menyediakan kedua cache objek dan cache bytecode. APCu adalah sebuah proyek untuk membawa APC
object cache PHP 5.5 +, karena PHP sekarang memiliki cache bytecode built-in (OPcache).

Learn more about popular object caching systems:

* [APCu](https://github.com/krakjoe/apcu)
* [APC Functions](http://php.net/manual/en/ref.apc.php)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [XCache APIs](http://xcache.lighttpd.net/wiki/XcacheApi)
* [WinCache Functions](http://www.php.net/manual/en/ref.wincache.php)
