---
isChild: true
anchor: test_driven_development
---

## Test Driven Development {#test_driven_development_title}

From [Wikipedia](http://en.wikipedia.org/wiki/Test-driven_development):

> Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: first the developer writes a failing automated test case that defines a desired improvement or new function, then produces code to pass that test and finally refactors the new code to acceptable standards. Kent Beck, who is credited with having developed or 'rediscovered' the technique, stated in 2003 that TDD encourages simple designs and inspires confidence

Ada beberapa jenis pengujian yang dapat Anda lakukan untuk aplikasi Anda

### Unit Testing

Unit Testing adalah pendekatan pemrograman untuk memastikan fungsi , kelas dan metode bekerja sebagai
diharapkan , dari titik Anda membangun mereka semua jalan melalui siklus pengembangan . dengan memeriksa
nilai-nilai akan masuk dan keluar dari berbagai fungsi dan metode , Anda dapat memastikan logika internal
bekerja dengan benar . Dengan menggunakan Dependency Injection dan membangun " tiruan " kelas dan bertopik Anda dapat memverifikasi bahwa dependensi yang benar digunakan untuk cakupan tes lebih baik .

Ketika Anda membuat sebuah kelas atau fungsi Anda harus membuat unit test untuk setiap perilaku itu harus memiliki . Pada tingkat yang sangat dasar Anda harus
membuat kesalahan yakin jika Anda mengirim argumen buruk dan pastikan bekerja jika Anda mengirim argumen yang valid .
Hal ini akan membantu memastikan bahwa ketika Anda membuat perubahan ke kelas ini atau fungsi nanti dalam pengembangan
siklus yang fungsi lama terus bekerja seperti yang diharapkan . Satu-satunya alternatif untuk ini akan menjadi
var_dump ( ) dalam test.php , yang ada cara untuk membangun sebuah aplikasi - besar atau kecil .

Penggunaan lainnya untuk tes unit memberikan kontribusi ke open source . Jika Anda dapat menulis sebuah tes yang menunjukkan rusak
fungsi ( yaitu gagal ) , kemudian memperbaikinya , dan menunjukkan tes passing , patch jauh lebih mungkin untuk dapat diterima . jika
Anda menjalankan sebuah proyek yang menerima permintaan menarik maka Anda harus menunjukkan ini sebagai suatu kebutuhan.

[ PHPUnit ] ( http://phpunit.de ) adalah kerangka pengujian de - facto untuk menulis unit test untuk PHP
aplikasi , tetapi ada beberapa alternatif

* [atoum](https://github.com/atoum/atoum)
* [Enhance PHP](https://github.com/Enhance-PHP/Enhance-PHP)
* [PUnit](http://punit.smf.me.uk/)
* [SimpleTest](http://simpletest.org)


### Integration Testing

From [Wikipedia](http://en.wikipedia.org/wiki/Integration_testing):

> Integration testing (sometimes called Integration and Testing, abbreviated "I&T") is the phase in software testing in which individual software modules are combined and tested as a group. It occurs after unit testing and before validation testing. Integration testing takes as its input modules that have been unit tested, groups them in larger aggregates, applies tests defined in an integration test plan to those aggregates, and delivers as its output the integrated system ready for system testing.

Banyak alat yang sama yang dapat digunakan untuk unit testing dapat digunakan untuk pengujian integrasi sebanyak
prinsip-prinsip yang sama digunakan.

### Functional Testing

Kadang-kadang juga dikenal sebagai pengujian penerimaan, uji fungsional terdiri dari menggunakan alat-alat untuk membuat otomatis
tes yang benar-benar menggunakan aplikasi Anda, bukan hanya memverifikasi bahwa unit individu kode berperilaku
benar dan bahwa unit individu dapat berbicara satu sama lain dengan benar. Alat-alat ini biasanya bekerja menggunakan real
data dan simulasi pengguna yang sebenarnya dari aplikasi.

#### Functional Testing Tools

* [Selenium](http://seleniumhq.com)
* [Mink](http://mink.behat.org)
* [Codeception](http://codeception.com) adalah kerangka pengujian penuh tumpukan yang meliputi alat pengujian penerimaan
* [Storyplayer](http://datasift.github.io/storyplayer) adalah kerangka pengujian penuh tumpukan yang meliputi dukungan untuk menciptakan dan menghancurkan lingkungan pengujian on demand
