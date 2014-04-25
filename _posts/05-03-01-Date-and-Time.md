---
title: Tanggal dan Waktu
isChild: true
anchor: date_and_time
---

## Tanggal dan Waktu {#date_and_time_title}

PHP memiliki kelas bernama DateTime untuk membantu Anda ketika membaca, menulis, atau menghitung membandingkan dengan tanggal dan waktu. ada
banyak tanggal dan waktu fungsi dalam PHP terkait selain DateTime, tetapi menyediakan antarmuka yang bagus berorientasi obyek untuk sebagian
penggunaan umum. Ia bisa menangani zona waktu, tapi itu di luar pengenalan singkat ini.

Untuk mulai bekerja dengan DateTime, mengubah tanggal dan waktu baku string untuk obyek dengan `createFromFormat ()` metode pabrik
atau melakukan `baru \ DateTime` untuk mendapatkan tanggal dan waktu. Gunakan format () metode `` untuk mengkonversi DateTime kembali ke string untuk output.

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('m/d/Y') . "\n";
{% endhighlight %}

Menghitung dengan DateTime adalah mungkin dengan kelas DateInterval. DateTime memiliki metode seperti `add ()` dan `sub ()` yang
mengambil DateInterval sebagai argumen. Jangan menulis kode yang mengharapkan jumlah yang sama detik setiap hari, baik siang hari
tabungan dan zona waktu perubahan akan mematahkan asumsi tersebut. Gunakan interval tanggal gantinya. Untuk menghitung tanggal penggunaan perbedaan
yang `diff ()` metode. Ini akan mengembalikan DateInterval baru, yang super mudah untuk menampilkan.

{% highlight php %}
<?php
// create a copy of $start and add one month and 6 days
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Difference: ' . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Difference: 1 month, 6 days (total: 37 days)
{% endhighlight %}

On DateTime objects you can use standard comparison:
{% highlight php %}
<?php
if ($start < $end) {
    echo "Start is before end!\n";
}
{% endhighlight %}

Salah satu contoh terakhir untuk menunjukkan kelas DatePeriod. Hal ini digunakan untuk beralih di atas berulang peristiwa. Hal ini dapat mengambil dua Objek DateTime, awal dan akhir, dan interval yang akan mengembalikan semua peristiwa di antara.


{% highlight php %}
<?php
// output all thursdays between $start and $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // output each date in the period
    echo $date->format('m/d/Y') . ' ';
}
{% endhighlight %}

* [Baca tentang DateTime][datetime]
* [Baca tentang DateTime formatting][dateformat] (tanggal diterima opsi format string)

[datetime]: http://www.php.net/manual/book.datetime.php
[dateformat]: http://www.php.net/manual/function.date.php
