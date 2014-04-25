---
title: Konsep Dasar
isChild: true
anchor: basic_concept
---

## Konsep Dasar {#basic_concept_title}

Kita dapat menunjukkan konsep dengan contoh sederhana, namun naif.

Di sini kita memiliki `database` kelas yang memerlukan adaptor untuk berbicara dengan database. Kami instantiate
adaptor dalam konstruktor dan menciptakan ketergantungan keras. Hal ini membuat pengujian sulit dan berarti `database` kelas
sangat erat digabungkan ke adaptor.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct()
    {
        $this->adapter = new MySqlAdapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

Kode ini dapat refactored untuk menggunakan Dependency Injection dan karenanya melonggarkan ketergantungan.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(MySqlAdapter $adapter)
    {
        $this->adapter = $adapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

Sekarang kita memberikan `database` class ketergantungan daripada itu menciptakan itu sendiri. Kita bahkan bisa menciptakan sebuah metode
yang akan menerima argumen dari ketergantungan dan mengatur seperti itu, atau jika `$ adaptor` properti adalah `publik` kita bisa
mengaturnya secara langsung.
