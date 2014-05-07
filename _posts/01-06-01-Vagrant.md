---
isChild: true
anchor: vagrant
---

## Vagrant {#vagrant_title}

Seringkali _developer_ menemukan masalah ketika menjalankan aplikasi pada saat _development_ dan _production_.
Masalah itu ditimbulkan karena perbedaan environment. Misalkan _developer_ membuat aplikasi di Windows, 
sedangkan server produksi menggunakan Linux.

Masalah tersebut semakin terasa ketika anda bekerja dalam tim di mana setiap anggota menggunakan OS yang berbeda-beda.
Satu orang menggunakan Windows, satu orang menyukai MacOS, dan lainnya memilih Linux.

Jika itulah yang Anda alami, mungkin ada baiknya Anda mempertimbangkan menggunakan mesin virtual dalam _development_.
Kedengarannya rumit, tapi dengan menggunakan [Vagrant], Anda dapat dengan mudah mengatur 
mesin virtual hanya dalam beberapa langkah. 

Mesin virtual ini kemudian dapat diatur secara manual, atau Anda dapat menggunakan "provisioning"
software seperti [Puppet] atau [Chef] untuk melakukannya. Provisioning mesin virtual adalah cara yang bagus untuk
memastikan bahwa beberapa mesin ditetapkan dalam cara yang identik. Dan menghilangkan kebutuhan bagi Anda untuk 
men-setup nya secara manual. Anda bahkan dapat dengan mudah menghapus mesin virtual tersebut dan membuatnya lagi 
dari awal.

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
