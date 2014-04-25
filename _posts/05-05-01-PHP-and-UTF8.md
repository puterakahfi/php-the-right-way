---
title: PHP dan UTF-8
isChild: true
anchor: php_and_utf8
---

## PHP dan UTF-8 {#php_and_utf8_title}

Bagian _this awalnya ditulis oleh [Alex Cabal] (https://alexcabal.com/) ke arah
[PHP Praktik Terbaik] (https://phpbestpractices.org/ # utf-8) dan kini telah bersama here_.

### Tidak ada satu baris. Hati-hati, detail, dan konsisten.

Saat ini PHP tidak mendukung Unicode pada tingkat yang rendah. Ada beberapa cara untuk memastikan bahwa UTF-8 string diproses OK,
tapi itu tidak mudah, dan membutuhkan menggali ke hampir semua tingkat aplikasi web, dari HTML ke SQL ke PHP. Kami akan bertujuan
untuk singkat, ringkasan praktis.

### UTF-8 di level PHP

Operasi string dasar, seperti concatenating dua string dan menetapkan string ke variabel, tidak perlu apa-apa
khusus untuk UTF-8. Namun sebagian besar fungsi string, seperti `strpos ()` dan `strlen ()`, perlu pertimbangan khusus. ini
fungsi sering memiliki mitra `mb_ *`: misalnya, `mb_strpos ()` dan `mb_strlen ()`. Bersama-sama, mitra ini
fungsi disebut Fungsi multibita String. Fungsi multibyte string yang secara khusus dirancang untuk
beroperasi pada string Unicode.

Anda harus menggunakan `mb_ *` fungsi setiap kali Anda beroperasi pada string Unicode. Sebagai contoh, jika Anda menggunakan `substr ()` pada
UTF-8 string, ada kesempatan baik hasilnya akan mencakup beberapa kacau setengah karakter. Fungsi yang benar untuk menggunakan
akan menjadi mitra multibyte, `mb_substr ()`.

Bagian yang sulit adalah mengingat untuk menggunakan `mb_ *` fungsi setiap saat. Jika Anda lupa bahkan hanya sekali, Unicode Anda
string yang memiliki kesempatan menjadi kacau selama pemrosesan lebih lanjut.

Tidak semua fungsi string memiliki mitra `mb_ *`. Jika tidak ada satu untuk apa yang ingin Anda lakukan, maka Anda mungkin akan keluar
keberuntungan.

Selain itu, Anda harus menggunakan `mb_internal_encoding ()` fungsi di bagian atas setiap script PHP Anda menulis (atau di
atas global Anda termasuk script), dan `mb_http_output ()` fungsi tepat setelah itu jika skrip Anda keluaran untuk
browser. Secara eksplisit mendefinisikan pengkodean string Anda dalam setiap naskah akan menghemat banyak sakit kepala bawah
jalan.

Akhirnya, banyak fungsi PHP yang beroperasi pada string memiliki parameter opsional membiarkan Anda menentukan karakter
encoding. Anda harus selalu secara eksplisit menunjukkan UTF-8 ketika diberi pilihan. Sebagai contoh, `htmlentities ()` memiliki
pilihan untuk encoding karakter, dan Anda harus selalu menentukan UTF-8 jika berurusan dengan string tersebut.

Perhatikan bahwa pada PHP 5.4.0, UTF-8 adalah encoding default untuk `htmlentities ()` dan `htmlspecialchars ()`.


### UTF-8 di level Database

Jika script PHP Anda mengakses MySQL, ada kemungkinan string Anda dapat disimpan sebagai non-UTF-8 string dalam database
bahkan jika Anda mengikuti semua tindakan pencegahan di atas.

Untuk memastikan string Anda pergi dari PHP ke MySQL sebagai UTF-8, pastikan database dan tabel semua diatur ke
`utf8mb4` set karakter dan pemeriksaan, dan bahwa Anda menggunakan `utf8mb4` set karakter di PDO connection string. lihat
contoh kode di bawah ini. Ini _critically important_.

Perhatikan bahwa Anda harus menggunakan `utf8mb4` character set untuk dukungan UTF-8 selesai, bukan `utf8` set karakter! lihat
Bacaan lebih lanjut mengapa.

### UTF-8 di level Web Browser

Gunakan `mb_http_output ()` fungsi untuk memastikan bahwa script PHP Anda output UTF-8 string ke browser Anda. Dalam HTML Anda,
termasuk [charset `<meta>` tag] (http://htmlpurifier.org/docs/enduser-utf8.html) di `<head>` tag halaman Anda.

{% highlight php %}
<?php
// Tell PHP that we're using UTF-8 strings until the end of the script
mb_internal_encoding('UTF-8');
 
// Tell PHP that we'll be outputting UTF-8 to the browser
mb_http_output('UTF-8');
 
// Our UTF-8 test string
$string = 'Êl síla erin lû e-govaned vîn.';
 
// Transform the string in some way with a multibyte function
// Note how we cut the string at a non-Ascii character for demonstration purposes
$string = mb_substr($string, 0, 15);
 
// Connect to a database to store the transformed string
// See the PDO example in this document for more information
// Note the `set names utf8mb4` commmand!
$link = new \PDO(   
                    'mysql:host=your-hostname;dbname=your-db;charset=utf8mb4',
                    'your-username',
                    'your-password',
                    array(
                        \PDO::ATTR_ERRMODE => \PDO::ERRMODE_EXCEPTION,
                        \PDO::ATTR_PERSISTENT => false
                    )
                );
 
// Store our transformed string as UTF-8 in our database
// Your DB and tables are in the utf8mb4 character set and collation, right?
$handle = $link->prepare('insert into ElvishSentences (Id, Body) values (?, ?)');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->bindValue(2, $string);
$handle->execute();
 
// Retrieve the string we just stored to prove it was stored correctly
$handle = $link->prepare('select * from ElvishSentences where Id = ?');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->execute();
 
// Store the result into an object that we'll output later in our HTML
$result = $handle->fetchAll(\PDO::FETCH_OBJ);
?><!doctype html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title>UTF-8 test page</title>
    </head>
    <body>
        <?php
        foreach($result as $row){
            print($row->Body);  // This should correctly output our transformed UTF-8 string to the browser
        }
        ?>
    </body>
</html>
{% endhighlight %}

### Bacaan Lebih Lanjut

* [PHP Manual: String Operations](http://php.net/manual/en/language.operators.string.php)
* [PHP Manual: String Functions](http://php.net/manual/en/ref.strings.php)
    * [`strpos()`](http://php.net/manual/en/function.strpos.php)
    * [`strlen()`](http://php.net/manual/en/function.strlen.php)
    * [`substr()`](http://php.net/manual/en/function.substr.php)
* [PHP Manual: Multibyte String Functions](http://php.net/manual/en/ref.mbstring.php)
    * [`mb_strpos()`](http://php.net/manual/en/function.mb-strpos.php)
    * [`mb_strlen()`](http://php.net/manual/en/function.mb-strlen.php)
    * [`mb_substr()`](http://php.net/manual/en/function.mb-substr.php)
    * [`mb_internal_encoding()`](http://php.net/manual/en/function.mb-internal-encoding.php)
    * [`mb_http_output()`](http://php.net/manual/en/function.mb-http-output.php)
    * [`htmlentities()`](http://php.net/manual/en/function.htmlentities.php)
    * [`htmlspecialchars()`](http://www.php.net/manual/en/function.htmlspecialchars.php)
* [PHP UTF-8 Cheatsheet](http://blog.loftdigital.com/blog/php-utf-8-cheatsheet)
* [Stack Overflow: What factors make PHP Unicode-incompatible?](http://stackoverflow.com/questions/571694/what-factors-make-php-unicode-incompatible)
* [Stack Overflow: Best practices in PHP and MySQL with international strings](http://stackoverflow.com/questions/140728/best-practices-in-php-and-mysql-with-international-strings)
* [How to support full Unicode in MySQL databases](http://mathiasbynens.be/notes/mysql-utf8mb4)
* [Brining Unicode to PHP with Portable UTF-8](http://www.sitepoint.com/bringing-unicode-to-php-with-portable-utf8/)
