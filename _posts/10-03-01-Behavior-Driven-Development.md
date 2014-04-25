---
isChild: true
anchor: behavior_driven_development
---

## Behavior Driven Development {#behavior_driven_development_title}

Ada dua jenis Perilaku-Driven Development (BDD): SpecBDD dan StoryBDD. SpecBDD berfokus pada perilaku teknis kode, sementara StoryBDD berfokus pada bisnis atau fitur perilaku atau interaksi. PHP memiliki kerangka kerja untuk kedua jenis BDD.

Dengan StoryBDD, Anda menulis cerita terbaca-manusia yang menggambarkan perilaku aplikasi Anda. cerita-cerita ini
kemudian dapat dijalankan sebagai tes yang sebenarnya terhadap aplikasi Anda. Kerangka yang digunakan dalam aplikasi PHP untuk StoryBDD
adalah Behat, yang terinspirasi oleh [Ketimun] (http://cukes.info/) proyek Ruby dan menerapkan DSL Gherkin
untuk menggambarkan perilaku fitur.

Dengan SpecBDD, Anda menulis spesifikasi yang menggambarkan bagaimana kode Anda yang sebenarnya harus bersikap. Alih-alih pengujian
fungsi atau metode, Anda gambarkan bagaimana fungsi atau metode harus bersikap. PHP menawarkan kerangka PHPSpec untuk tujuan ini. Kerangka kerja ini terinspirasi
oleh [RSpec proyek] (http://rspec.info/) untuk Ruby.

### BDD Links

* [Behat](http://behat.org/), kerangka StoryBDD untuk PHP, terinspirasi oleh Ruby [Cucumber](http://cukes.info/) project;
* [PHPSpec](http://www.phpspec.net/), kerangka SpecBDD untuk PHP, terinspirasi oleh Ruby [RSpec](http://rspec.info/) project;
* [Codeception](http://www.codeception.com) adalah kerangka pengujian penuh tumpukan yang menggunakan prinsip BDD.
