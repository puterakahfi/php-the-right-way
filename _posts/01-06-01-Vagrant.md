---
isChild: true
anchor: vagrant
---

## Vagrant {#vagrant_title}

Menjalankan aplikasi Anda pada lingkungan yang berbeda dalam pengembangan dan produksi dapat menyebabkan bug aneh
muncul ketika Anda pergi hidup. Ini juga sulit untuk menjaga lingkungan pembangunan yang berbeda up to date dengan sama
Versi untuk semua pustaka yang digunakan ketika bekerja dengan tim pengembang.

Jika Anda mengembangkan di Windows dan menggunakan untuk Linux (atau apa pun non-Windows) atau sedang mengembangkan dalam sebuah tim, Anda
harus mempertimbangkan menggunakan mesin virtual. Ini terdengar rumit, tapi menggunakan [Vagrant] [gelandangan] Anda dapat mengatur sederhana
mesin virtual dengan hanya beberapa langkah. Kotak dasar ini kemudian dapat diatur secara manual, atau Anda dapat menggunakan "pengadaan"
software seperti [Wayang] [wayang] atau [Chef] [chef] untuk melakukan ini untuk Anda. Provisioning kotak dasar adalah cara yang bagus untuk
memastikan bahwa beberapa kotak ditetapkan dalam cara yang identik dan menghilangkan kebutuhan bagi Anda untuk menjaga rumit
"set up" daftar perintah. Anda juga bisa "menghancurkan" kotak dasar Anda dan menciptakan tanpa banyak langkah manual, sehingga
mudah untuk membuat "fresh" instalasi.

Vagrant menciptakan shared folder yang digunakan untuk berbagi kode antara host dan mesin virtual Anda, yang berarti Anda dapat
membuat dan mengedit file Anda pada mesin host Anda dan kemudian menjalankan kode di dalam mesin virtual Anda.

### Bantuan Singkat

Jika Anda perlu sedikit bantuan untuk mulai menggunakan Vagrant ada tiga layanan yang mungkin berguna:

- [Rove][rove]: layanan yang memungkinkan Anda untuk pregenerate khas Vagrant membangun, PHP antara pilihan. itu
  penyediaan dibuat dengan Chef.
- [Puphpet][puphpet]: GUI sederhana untuk mengatur mesin virtual untuk pengembangan PHP. ** Berat fokus di PHP **. selain
  VMs lokal, dapat digunakan untuk menyebarkan awan layanan juga. Provisi ini dibuat dengan Wayang.
- [Protobox][protobox]: adalah lapisan di atas vagrant dan GUI web untuk setup mesin virtual untuk pengembangan web. Sebuah dokumen YAML tunggal mengendalikan segala sesuatu yang diinstal pada mesin virtual.

[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
[rove]: http://rove.io/
[puphpet]: https://puphpet.com/
[protobox]: http://getprotobox.com/
