---
isChild: true
anchor: building_and_deploying_your_application
---

## Building dan Deploying {#building_and_deploying_your_application_title}

Jika Anda menemukan diri Anda melakukan petunjuk basis data perubahan skema atau menjalankan tes secara manual sebelum memperbarui file Anda
(manual), berpikir dua kali! Dengan setiap tugas petunjuk tambahan yang diperlukan untuk menyebarkan versi baru dari aplikasi Anda, peluang untuk
kesalahan fatal meningkat. Apakah Anda sedang berhadapan dengan update sederhana, proses membangun komprehensif atau
bahkan strategi integrasi berkesinambungan, [membangun otomatisasi] (http://en.wikipedia.org/wiki/Build_automation) adalah Anda
teman.

Di antara tugas-tugas Anda mungkin ingin untuk mengotomatisasi adalah:

* Ketergantungan manajemen
* Kompilasi, minification aset Anda
* Menjalankan tes
* Penciptaan dokumentasi
* Kemasan
* Deployment


### Build Automation Tools

Membangun alat dapat digambarkan sebagai kumpulan skrip yang menangani tugas-tugas umum dari penyebaran perangkat lunak . membangun
alat bukan merupakan bagian dari perangkat lunak Anda , itu bekerja pada perangkat lunak Anda dari ' luar ' .

Ada banyak tools open source yang tersedia untuk membantu Anda dengan membangun otomatisasi , beberapa ditulis dalam PHP yang lain tidak .
Hal ini seharusnya tidak menghambat Anda dari menggunakan mereka , jika mereka lebih cocok untuk pekerjaan tertentu . Berikut adalah beberapa contoh :

[ Phing ] ( http://www.phing.info/ ) adalah cara termudah untuk memulai dengan penyebaran otomatis di dunia PHP . dengan
Phing Anda dapat mengontrol kemasan , penyebaran atau proses pengujian dari dalam sederhana membangun file XML . Phing (yang
didasarkan pada [ Apache Ant ] ( http://ant.apache.org/ ) ) menyediakan kaya set tugas biasanya diperlukan untuk menginstal atau memperbarui
aplikasi web dan dapat diperpanjang dengan tugas-tugas tambahan lain , yang ditulis dalam PHP .

[ Capistrano ] ( https://github.com/capistrano/capistrano/wiki ) adalah sistem untuk * menengah hingga lanjutan programmer * untuk
mengeksekusi perintah dengan cara yang terstruktur berulang pada satu atau lebih mesin remote . Hal ini pra - dikonfigurasi untuk menyebarkan
Ruby on Rails aplikasi , namun orang ** berhasil menyebarkan sistem PHP ** dengan itu . Keberhasilan penggunaan
Capistrano tergantung pada pengetahuan tentang Ruby dan Rake .

Posting blog dave Gardner [ PHP Deployment dengan Capistrano ] ( http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/ )
adalah titik awal yang baik untuk pengembang PHP tertarik Capistrano .

[ Chef ] ( http://www.opscode.com/chef/ ) lebih dari kerangka penyebaran , itu adalah sistem berbasis Ruby sangat kuat
kerangka integrasi yang tidak hanya menyebarkan aplikasi Anda, tetapi dapat membangun lingkungan server seluruh atau kotak virtual.

Sumber daya koki untuk pengembang PHP :

* [ Tiga bagian blog seri tentang penggelaran aplikasi LAMP dengan Chef , gelandangan , dan EC2](http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/)
* [ Chef Cookbook yang menginstal dan mengkonfigurasi PHP 5.3 dan sistem manajemen paket PEAR ] ( https://github.com/opscode-cookbooks/php )

Bacaan lebih lanjut :

* [ Otomatis proyek Anda dengan Apache Ant ] ( http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/ )
* [ Maven ] ( http://maven.apache.org/ ) , kerangka membangun berdasarkan Ant dan [ bagaimana menggunakannya dengan PHP ] ( http://www.php-maven.org/ )

### Continuous Integration

> Continuous Integration is a software development practice where members of a team integrate their work frequently, 
> usually each person integrates at least daily — leading to multiple integrations per day. Many teams find that this 
> approach leads to significantly reduced integration problems and allows a team to develop cohesive software more 
> rapidly.

*-- Martin Fowler*

Ada berbagai cara untuk menerapkan integrasi berkesinambungan untuk PHP. Baru-baru ini [Travis CI] (https://travis-ci.org/) memiliki
melakukan pekerjaan yang besar membuat integrasi berkesinambungan kenyataan bahkan untuk proyek-proyek kecil. Travis CI adalah host kontinyu
layanan integrasi untuk komunitas open source. Hal ini terintegrasi dengan GitHub dan menawarkan dukungan kelas pertama bagi banyak
bahasa termasuk PHP.

Bacaan lebih lanjut:

* [Continuous Integration dengan Jenkins] (http://jenkins-ci.org/)
* [Continuous Integration dengan PHPCI] (http://www.phptesting.org/)
* [Continuous Integration dengan TeamCity] (http://www.jetbrains.com/teamcity/)

