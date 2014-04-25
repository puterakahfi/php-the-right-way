---
isChild: true
anchor: password_hashing
---

## Password Hashing {#password_hashing_title}

Akhirnya semua orang membangun aplikasi PHP yang bergantung pada pengguna login. Username dan password yang disimpan dalam database dan kemudian digunakan untuk autentikasi pengguna pada saat login.

Adalah penting bahwa Anda benar [_hash_] [3] password sebelum menyimpannya. Sandi hashing adalah ireversibel, fungsi salah satu cara yang dilakukan terhadap password user. Ini menghasilkan string tetap-panjang yang tidak memungkinkan untuk bisa terbalik. Ini berarti Anda dapat membandingkan hash terhadap yang lain untuk menentukan apakah mereka berdua datang dari sumber string yang sama, tetapi Anda tidak bisa menentukan string asli. Jika password tidak hash dan database Anda diakses oleh pihak ketiga yang tidak sah, semua akun pengguna sekarang dikompromikan. Beberapa pengguna mungkin (sayangnya) menggunakan password yang sama untuk layanan lainnya. Oleh karena itu, penting untuk mengambil keamanan serius.

**Hashing passwords dengan `password_hash`**

Dalam PHP 5.5 `password_hash` diperkenalkan. Pada saat ini adalah menggunakan BCrypt, algoritma terkuat saat ini didukung oleh PHP. Ini akan diperbarui di masa depan untuk mendukung lebih algoritma yang diperlukan sekalipun. The `password_compat` perpustakaan diciptakan untuk menyediakan kompatibilitas ke depan untuk PHP> = 5.3.7.

Di bawah ini kami hash string, dan kemudian memeriksa hash terhadap string baru. Karena kami dua string sumber yang berbeda ('rahasia-password' vs 'buruk-password') login ini akan gagal.

{% highlight php %}
<?php
                      
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    // Correct Password
} else {
    // Wrong password
}
{% endhighlight %}  



* [Learn about `password_hash`] [1]
* [`password_compat` for PHP  >= 5.3.7 && < 5.5] [2]
* [Learn about hashing in regards to cryptography] [3]
* [PHP `password_hash` RFC] [4]

[1]: http://us2.php.net/manual/en/function.password-hash.php
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash
