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

With the strategy pattern you encapsulate specific families of algorithms allowing the client class responsible for 
instantiating a particular algorithm to have no knowledge of the actual implementation.
There are several variations on the strategy pattern, the simplest of which is outlined below:

This first code snippet outlines a family of algorithms; you may want a serialized array, some JSON or maybe 
just an array of data:
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

By encapsulating the above algorithms you are making it nice and clear in your code that other developers can easily 
add new output types without affecting the client code.

You will see how each concrete 'output' class implements an OutputInterface - this serves two purposes, primarily it
provides a simple contract which must be obeyed by any new concrete implementations. Secondly by implementing a common
interface you will see in the next section that you can now utilise [Type Hinting](http://php.net/manual/en/language.oop5.typehinting.php) to ensure that the client which is utilising these behaviours is of the correct type in
this case 'OutputInterface'.

The next snippet of code outlines how a calling client class might use one of these algorithms and even better set the
behaviour required at runtime:
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

* [Strategy pattern on Wikipedia](http://en.wikipedia.org/wiki/Strategy_pattern)

## Front Controller

The front controller pattern is where you have a single entrance point for you web application (e.g. index.php) that
handles all of the requests. This code is responsible for loading all of the dependencies, processing the request and
sending the response to the browser. The front controller pattern can be beneficial because it encourages modular code
and gives you a central place to hook in code that should be run for every request (such as input sanitization).

* [Front Controller pattern on Wikipedia](https://en.wikipedia.org/wiki/Front_Controller_pattern)

## Model-View-Controller

The model-view-controller (MVC) pattern and its relatives HMVC and MVVM lets you break up code into logical objects that serve very specific purposes. Models serve as a data access layer where data is fetched and returned in formats usable throughout your application. Controllers handle the request, process the data returned from models and load views to send in the response. And views are display templates (markup, xml, etc) that are sent in the response to the web browser.

MVC is the most common architectural pattern used in the popular [PHP frameworks](https://github.com/codeguy/php-the-right-way/wiki/Frameworks).

Learn more about MVC and its relatives:

* [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93View%E2%80%93Controller)
* [HMVC](https://en.wikipedia.org/wiki/Hierarchical_model%E2%80%93view%E2%80%93controller)
* [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel)
