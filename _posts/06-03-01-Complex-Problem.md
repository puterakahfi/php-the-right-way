---
title: Masalah Kompleks
isChild: true
anchor: complex_problem
---

## Masalah Kompleks {#complex_problem_title}

Jika Anda pernah membaca tentang Dependency Injection maka Anda mungkin telah melihat istilah * "Inversion of Control" * atau * "Ketergantungan Inversi Prinsip" *.
Ini adalah masalah kompleks yang Dependency Injection memecahkan.

### Inversion of Control

Inversion of Control adalah seperti yang dikatakan, "pembalik kontrol" dari suatu sistem dengan menjaga kontrol organisasi yang sama sekali terpisah dari benda kami.
Dalam hal Dependency Injection, ini berarti melonggarkan ketergantungan kita dengan mengendalikan dan instantiating mereka di tempat lain dalam sistem.

Selama bertahun-tahun, kerangka kerja PHP telah mencapai Inversion of Control, namun, pertanyaannya menjadi, bagian mana dari kontrol
Anda pembalik, dan di mana? Sebagai contoh, kerangka kerja MVC umumnya akan memberikan objek atau basis pengendali super yang lain
pengendali harus memperpanjang untuk mendapatkan akses ke dependensinya. Ini ** adalah ** Inversion of Control, namun, bukannya melonggarkan
dependensi, metode ini hanya bergerak mereka.

Injeksi Ketergantungan memungkinkan kita untuk lebih elegan memecahkan masalah ini dengan hanya menyuntikkan dependensi yang kita butuhkan, ketika kita membutuhkan mereka,
tanpa perlu untuk setiap dependensi kode keras sama sekali.

### Dependency Inversion Principle

Ketergantungan Inversi Prinsip adalah "D" di set SOLID prinsip-prinsip desain berorientasi objek yang menyatakan orang harus
* "Tergantung pada Abstractions. Jangan tergantung pada konkret." *. Sederhananya, ini berarti ketergantungan kita harus interface / kontrak atau abstrak kelas daripada implementasi konkret. Kita dapat dengan mudah refactor contoh di atas untuk mengikuti prinsip ini.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(AdapterInterface $adapter)
    {
        $this->adapter = $adapter;
    }
}

interface AdapterInterface {}

class MysqlAdapter implements AdapterInterface {}
{% endhighlight %}

Ada beberapa manfaat bagi `database` class sekarang tergantung pada interface daripada concretion a.

Pertimbangkan bahwa Anda bekerja dalam tim dan adaptor sedang dikerjakan oleh seorang rekan. Dalam contoh pertama kita, kita akan memiliki
untuk menunggu rekan dikatakan menyelesaikan adaptor sebelum kita benar bisa mengejek itu untuk tes unit kami. Sekarang bahwa ketergantungan
adalah sebuah antarmuka / kontrak kita bisa bahagia mengejek antarmuka yang mengetahui bahwa rekan kami akan membangun adaptor berdasarkan kontrak itu.

Manfaat yang lebih besar untuk metode ini adalah bahwa kode kita sekarang jauh lebih scalable. Jika tahun ke depan kita memutuskan bahwa kita
ingin bermigrasi ke berbagai jenis database, kita dapat menulis sebuah adaptor yang mengimplementasikan antarmuka asli dan menyuntikkan bahwa alih-alih, tidak lebih refactoring akan diperlukan seperti yang kita dapat memastikan bahwa adaptor mengikuti kontrak yang ditetapkan oleh antarmuka.
