---
isChild: true
anchor: exceptions
---

## Exceptions {#exceptions_title}

Pengecualian adalah bagian standar dari kebanyakan bahasa pemrograman populer, tetapi mereka sering diabaikan oleh programmer PHP .
Bahasa seperti Ruby sangat Exception berat , sehingga setiap kali sesuatu yang tidak beres seperti permintaan HTTP gagal , atau
query DB tidak beres , atau bahkan jika aset gambar tidak dapat ditemukan , Ruby ( atau permata yang digunakan ) akan memunculkan
pengecualian ke layar berarti Anda langsung tahu ada kesalahan .

PHP itu sendiri cukup longgar dengan hal ini , dan panggilan untuk ` file_get_contents ( ) ` akan biasanya hanya mendapatkan Anda ` PALSU ` dan peringatan .
Banyak kerangka PHP yang lebih tua seperti CodeIgniter hanya akan kembali palsu , log pesan ke log milik mereka dan mungkin
membiarkan Anda menggunakan metode seperti ` $ this - > meng-upload - > get_error ( ) ` untuk melihat apa yang salah . Masalahnya di sini adalah bahwa Anda harus pergi
mencari kesalahan dan memeriksa dokumentasi untuk melihat apa metode kesalahan adalah untuk kelas ini , bukan karena itu dibuat sangat
jelas .

Masalah lain adalah ketika kelas secara otomatis melempar kesalahan ke layar dan keluar dari proses. Ketika Anda melakukan ini, Anda
menghentikan pengembang lain dari mampu secara dinamis menangani kesalahan itu . Pengecualian harus dibuang untuk membuat pengembang
menyadari kesalahan ; mereka kemudian dapat memilih cara untuk menangani hal ini . mis :

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // The validation failed
}
catch(Fuel\Email\SendingFailedException $e)
{
    // The driver could not send the email
}
finally
{
    // Executed regardless of whether an exception has been thrown, and before normal execution resumes
}
{% endhighlight %}

### SPL Exceptions

Generik `Exception` kelas menyediakan sangat sedikit konteks debugging untuk pengembang; Namun, untuk memperbaiki hal ini,
adalah mungkin untuk menciptakan `Exception` jenis khusus oleh sub-klasifikasi generik `` Exception class:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

Ini berarti Anda dapat menambahkan beberapa blok catch dan menangani Pengecualian berbeda berbeda. Hal ini dapat menyebabkan
penciptaan banyak <em> </ em> Pengecualian kustom, beberapa di antaranya bisa dihindari dengan menggunakan Pengecualian SPL
disediakan dalam [SPL extension] [splext].

Jika misalnya Anda menggunakan `__call ()` Metode Sihir dan metode yang tidak valid diminta maka bukannya melemparkan standar
Exception yang tidak jelas, atau membuat Exception kustom hanya untuk itu, Anda hanya bisa `melempar BadMethodCallException baru;`.

* [Baca tentang Exceptions][exceptions]
* [Baca tentang SPL Exceptions][splexe]
* [Nesting Exceptions di PHP][nesting-exceptions-in-php]
* [Exception Best Practices di PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/en/language.exceptions.php
[splexe]: http://php.net/manual/en/spl.exceptions.php
[splext]: /#standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
