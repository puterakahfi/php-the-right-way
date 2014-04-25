---
isChild: true
anchor: bytecode_cache
---

## Bytecode Cache {#bytecode_cache_title}

Bila file PHP dijalankan , di bawah tenda itu pertama kali dikompilasi untuk bytecode ( juga dikenal sebagai opcode ) dan , hanya kemudian , bytecode dijalankan .
Jika sebuah file PHP tidak diubah , bytecode akan selalu sama . Ini berarti bahwa langkah kompilasi adalah pemborosan sumber daya CPU .

Di sinilah Bytecode Cache masuk Ini mencegah kompilasi berlebihan dengan menyimpan bytecode dalam memori dan menggunakan kembali pada panggilan berturut-turut .
Menyiapkan bytecode cache hitungan menit , dan aplikasi Anda akan mempercepat secara signifikan . Ada benar-benar ada alasan untuk tidak menggunakannya .

Pada PHP 5.5 , ada cache bytecode built -in yang disebut [ OPcache ] ( http://php.net/manual/en/book.opcache.php ) . ini adalah
juga tersedia untuk versi sebelumnya .

Lain populer bytecode cache adalah :

* [ APC ] ( http://php.net/manual/en/book.apc.php ) ( PHP 5.4 dan sebelumnya )
* [ XCache ] ( http://xcache.lighttpd.net/ )
* [ Zend Optimizer + ] ( http://www.zend.com/products/server/ ) ( bagian dari paket Server Zend )
* [ WinCache ] ( http://www.iis.net/download/wincacheforphp ) ( ekstensi untuk MS Windows Server )
