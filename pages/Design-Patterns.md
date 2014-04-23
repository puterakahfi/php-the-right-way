---
layout: page
title: Design Patterns
---

# Design Patterns

Ada banyak cara untuk men-struktur kode dalam sebuah project website, dan Anda dapat meletakkan arsitektur
sesuka anda. Namun, mengikuti standard pola / pattern yang sudah banyak digunakan adalah sebuah ide bagus.
Karena hal tersebut akan membuat kode Anda lebih mudah di-maintain dan lebih mudah dibaca oleh orang lain.

* [Architectural pattern on Wikipedia](https://en.wikipedia.org/wiki/Architectural_pattern)
* [Software design pattern on Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern)

## Factory

Salah satu design pattern yang sering digunakan yaitu Factory Pattern. Dalam pattern ini, sebuah class
bertugas untuk membuat instance / object yang diinginkan. Coba ikuti contoh di bawah ini:

{% highlight php %}
<?php
class Automobile
{
    private $vehicle_make;
    private $vehicle_model;

    public function __construct($make, $model)
    {
        $this->vehicle_make = $make;
        $this->vehicle_model = $model;
    }

    public function get_make_and_model()
    {
        return $this->vehicle_make . ' ' . $this->vehicle_model;
    }
}

class AutomobileFactory
{
    public static function create($make, $model)
    {
        return new Automobile($make, $model);
    }
}

// have the factory create the Automobile object
$veyron = AutomobileFactory::create('Bugatti', 'Veyron');

print_r($veyron->get_make_and_model()); // outputs "Bugatti Veyron"
{% endhighlight %}

Kode ini menggunakan factory pattern untuk membuat Automobile object. Ada 2 kelebihan dalam membangun kode
dengan cara seperti ini; pertama, jika nanti Anda ingin mengubah atau mengganti Automobile class Anda dapat
melakukannya dengan mudah hanya dengan cara mengubah class Factory, bukannya dengan mengganti semua kode yang
tersebar untuk membuat object. Kelebihan kedua, jika membuat instance object tersebut sangat rumit, anda 
dapat melakukan pekerjaan rumit tersebut di dalam class factory, bukannya mengulang-ulang pekerjaan rumit
tersebut di setiap tempat.

Menggunakan factory pattern tidaklah sebuah keharusan. Contoh kode yang dipakai di sini adalah kasus sederhana.
Namun jika Anda membuat project yang sangat kompleks, mungkin anda akan menghemat banyak waktu dengan
menggunakan factory pattern.

* [Factory pattern on Wikipedia](https://en.wikipedia.org/wiki/Factory_pattern)

## Singleton

Ketika mendesain sebuah aplikasi, biasanya dibutuhkan sebuah object yang hanya boleh ada satu kali dalam 
berjalannya proses tersebut. Singleton pattern akan membantu kita untuk melakukan hal itu.

{% highlight php %}
<?php
class Singleton
{
    /**
     * Returns the *Singleton* instance of this class.
     *
     * @staticvar Singleton $instance The *Singleton* instances of this class.
     *
     * @return Singleton The *Singleton* instance.
     */
    public static function getInstance()
    {
        static $instance = null;
        if (null === $instance) {
            $instance = new static();
        }

        return $instance;
    }

    /**
     * Protected constructor to prevent creating a new instance of the
     * *Singleton* via the `new` operator from outside of this class.
     */
    protected function __construct()
    {
    }

    /**
     * Private clone method to prevent cloning of the instance of the
     * *Singleton* instance.
     *
     * @return void
     */
    private function __clone()
    {
    }

    /**
     * Private unserialize method to prevent unserializing of the *Singleton*
     * instance.
     *
     * @return void
     */
    private function __wakeup()
    {
    }
}

class SingletonChild extends Singleton
{
}

$obj = Singleton::getInstance();
var_dump($obj === Singleton::getInstance());             // bool(true)

$anotherObj = SingletonChild::getInstance();
var_dump($anotherObj === Singleton::getInstance());      // bool(false)

var_dump($anotherObj === SingletonChild::getInstance()); // bool(true)
{% endhighlight %}

Kode di atas mengimplementasikan singleton pattern menggunakan static variable [*static* variable](http://php.net/language.variables.scope#language.variables.scope.static) dan static creation method `getInstance()`.
Perhatikan hal-hal berikut:

* The constructor [`__construct`](http://php.net/language.oop5.decon#object.construct) dideklarasikan sebagai protected untuk mencegah pembuatan object di luar singleton pattern.
* The magic method [`__clone`](http://php.net/language.oop5.cloning#object.clone) dideklarasikan sebagai private untuk mencegah clone melalui [`clone`](http://php.net/language.oop5.cloning) operator.
* The magic method [`__wakeup`](http://php.net/language.oop5.magic#object.wakeup) dideklarasikan sebagai private untuk mencegah unserializing sebuah object melalui global function [`unserialize()`](http://php.net/function.unserialize).
* Sebuah object baru dibuat melalui [late static binding](http://php.net/language.oop5.late-static-bindings) pada static method `getInstance()` dengan keyword `static`. Cara ini membuat kita memenuhi `Singleton` dalam contoh ini.

Singleton pattern berguna ketika kita perlu memastikan bahwa kita hanya memiliki satu instance dari class untuk seluruh
siklus hidup dalam aplikasi web. Hal ini biasanya terjadi ketika kita memiliki objek global (seperti konfigurasi sebuah
class) atau resource bersama (seperti antrian event).

Anda harus berhati-hati ketika menggunakan singleton pattern, seperti sifatnya memperkenalkan state global ke dalam
aplikasi, akan mengurangi testability. Dalam kebanyakan kasus, injeksi ketergantungan dapat (dan harus) 
digunakan di tempat dari kelas tunggal. Menggunakan injeksi ketergantungan berarti bahwa kita tidak 
memperkenalkan pasangan tidak perlu ke dalam desain aplikasi, sebagai obyek menggunakan resource bersama atau 
global membutuhkan pengetahuan tentang kelas didefinisikan secara konkret.

* [Singleton pattern di Wikipedia](https://en.wikipedia.org/wiki/Singleton_pattern)

## Strategy

Dengan strategy pattern, anda membungkus algoritma sejenis sehingga membuat class client 
bertanggung jawab untuk membuat instance dari sebuah algoritma spesifik tanpa perlu tahu implementasi
sesungguhnya. Ada beberapa variasi strategy pattern, salah satunya yang paling simpel yaitu:

Kode pertama menunjukkan keluarga algoritma; untuk serialize array, json, atau array of data:
{% highlight php %}
<?php

interface OutputInterface
{
    public function load();
}

class SerializedArrayOutput implements OutputInterface
{
    public function load()
    {
        return serialize($arrayOfData);
    }
}

class JsonStringOutput implements OutputInterface
{
    public function load()
    {
        return json_encode($arrayOfData);
    }
}

class ArrayOutput implements OutputInterface
{
    public function load()
    {
        return $arrayOfData;
    }
}
{% endhighlight %}

Dengan membungkus algoritma di atas Anda membuat itu bagus dan jelas dalam kode Anda bahwa pengembang lain dapat dengan mudah
menambahkan jenis keluaran baru tanpa mempengaruhi kode klien.

Anda akan melihat bagaimana masing-masing 'output' konkret class mengimplementasikan OutputInterface - ini melayani dua tujuan, terutama itu
memberikan kontrak sederhana yang harus dipatuhi oleh setiap implementasi beton baru. Kedua dengan menerapkan umum
antarmuka Anda akan melihat di bagian berikutnya bahwa sekarang Anda dapat memanfaatkan [Type Hinting] (http://php.net/manual/en/language.oop5.typehinting.php) untuk memastikan bahwa klien yang memanfaatkan perilaku ini adalah jenis yang tepat dalam
kasus ini 'OutputInterface'.

Potongan kode yang berikutnya menguraikan bagaimana kelas client memanggil mungkin menggunakan salah satu 
algoritma ini dan bahkan lebih baik mengatur perilaku yang diperlukan pada saat runtime:
{% highlight php %}
<?php

class SomeClient
{
    private $output;

    public function setOutput(OutputInterface $outputType)
    {
        $this->output = $outputType;
    }

    public function loadOutput()
    {
        return $this->output->load();
    }
}
{% endhighlight %}

The calling client class above has a private property which must be set at runtime and be of type 'OutputInterface'
once this property is set a call to loadOutput() will call the load() method in the concrete class of the output type
that has been set.
{% highlight php %}
<?php

$client = new SomeClient();

// Want an array?
$client->setOutput(new ArrayOutput());
$data = $client->loadOutput();

// Want some JSON?
$client->setOutput(new JsonStringOutput());
$data = $client->loadOutput();

{% endhighlight %}

* [Strategy pattern di Wikipedia](http://en.wikipedia.org/wiki/Strategy_pattern)

## Front Controller

Pola Controller depan adalah di mana Anda memiliki titik pintu masuk tunggal untuk aplikasi web Anda (misalnya index.php) yang
menangani semua permintaan. Kode ini bertanggung jawab untuk memuat semua dependensi, memproses permintaan dan
mengirim respon ke browser. Pola Controller depan dapat bermanfaat karena mendorong kode modular
dan memberikan Anda sebuah tempat sentral untuk menghubungkan dalam kode yang harus dijalankan untuk setiap permintaan (seperti input sanitasi).

* [Front Controller pattern di Wikipedia](https://en.wikipedia.org/wiki/Front_Controller_pattern)

## Model-View-Controller

Model-view-controller (MVC) pola dan kerabat HMVC dan MVVM memungkinkan Anda memecah kode ke objek logis yang melayani tujuan yang sangat spesifik. Model berfungsi sebagai lapisan akses data dimana data diambil dan dikembalikan dalam format yang dapat digunakan di seluruh aplikasi Anda. Controller menangani permintaan, proses data kembali dari model dan pandangan beban untuk mengirimkan respon. Dan pandangan tampilan template (markup, xml, dll) yang dikirim dalam penanggulangan browser web.

MVC adalah arsitektur paling sering dijumpai pada framework PHP modern [PHP frameworks](https://github.com/codeguy/php-the-right-way/wiki/Frameworks).

Pelajari lebih lanjut tentang MVC dan kerabat:

* [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93View%E2%80%93Controller)
* [HMVC](https://en.wikipedia.org/wiki/Hierarchical_model%E2%80%93view%E2%80%93controller)
* [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel)
