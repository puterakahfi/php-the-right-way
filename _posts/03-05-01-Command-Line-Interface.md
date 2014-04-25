---
isChild: true
anchor: command_line_interface
---

## Command Line Interface {#command_line_interface_title}

PHP diciptakan terutama untuk menulis aplikasi web, tetapi juga berguna untuk scripting baris perintah interface (CLI) program. Program baris perintah PHP dapat membantu Anda mengotomatisasi tugas-tugas umum seperti pengujian, penyebaran, dan aplikasi administrivia.

Program CLI PHP yang kuat karena Anda dapat menggunakan kode aplikasi Anda secara langsung tanpa harus membuat dan mengamankan web GUI untuk itu. Hanya pastikan untuk tidak menempatkan script CLI PHP di akar web publik Anda!

Coba jalankan PHP dari baris perintah Anda:

{% highlight bash %}
> php -i
{% endhighlight %}

The `-i` option akan mencetak konfigurasi PHP Anda seperti [phpinfo ``] [phpinfo] fungsi.

Mari kita menulis "Hello, $ name" Program CLI sederhana. Untuk mencobanya, membuat file bernama `hello.php`, seperti di bawah ini.

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}

PHP set up dua variabel khusus berdasarkan argumen naskah Anda dijalankan dengan. [`$` argc] [argc] adalah variabel integer yang berisi argumen * count * dan [`$ argv`] [argv] adalah variabel array yang berisi nilai * setiap argumen *. Argumen pertama selalu nama file script PHP Anda, dalam hal ini `hello.php`.

The `exit ()` ekspresi digunakan dengan nomor non-nol untuk membiarkan shell tahu bahwa perintah gagal. Kode keluar yang umum digunakan dapat ditemukan [di sini] [exit-kode]

Untuk menjalankan script kita, di atas, dari baris perintah:

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [Pelajari tentang menjalankan PHP dari command line][php-cli]
 * [Pelajari tentang setting Windows untuk menjalankan PHP dari command line][php-cli-windows]

[phpinfo]: http://php.net/manual/en/function.phpinfo.php
[cli-options]: http://www.php.net/manual/en/features.commandline.options.php
[argc]: http://php.net/manual/en/reserved.variables.argc.php
[argv]: http://php.net/manual/en/reserved.variables.argv.php
[php-cli]: http://php.net/manual/en/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/en/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits
