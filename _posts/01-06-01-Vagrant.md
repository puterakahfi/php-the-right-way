---
isChild: true
anchor: vagrant
---

## Vagrant {#vagrant_title}

Seringkali _developer_ menemukan masalah ketika menjalankan aplikasi pada saat _development_ dan _production_.
Masalah itu ditimbulkan karena perbedaan environment. Misalkan _developer_ membuat aplikasi di Windows, 
sedangkan server produksi menggunakan Linux.

Masalah tersebut semakin terasa ketika anda bekerja dalam sebuah tim di mana setiap anggota 
menggunakan OS yang berbeda-beda. Salah seorang menggunakan Windows, satu orang menyukai MacOS, dan lainnya memilih Linux.

Jika itulah yang Anda alami, mungkin ada baiknya Anda mempertimbangkan menggunakan mesin virtual dalam _development_.
Kedengarannya rumit, tapi dengan menggunakan [Vagrant], Anda dapat dengan mudah mengatur 
mesin virtual hanya dalam beberapa langkah. 

Mesin virtual ini kemudian dapat diatur secara manual, atau Anda dapat menggunakan "provisioning"
software seperti [Puppet] atau [Chef] untuk melakukannya. _Provisioning_ mesin virtual adalah cara yang bagus untuk
memastikan bahwa beberapa mesin ditetapkan dalam cara yang identik. Dan menghilangkan kebutuhan bagi Anda untuk 
men-setup nya secara manual. Anda bahkan dapat dengan mudah menghapus mesin virtual tersebut dan membuatnya lagi 
dari awal.

Vagrant menciptakan shared folder yang digunakan untuk berbagi kode antara host dan mesin virtual Anda, yang berarti Anda dapat
membuat dan mengedit file Anda pada mesin host Anda dan kemudian menjalankan kode di dalam mesin virtual Anda.

### Bantuan Singkat

Jika Anda perlu sedikit bantuan untuk mulai menggunakan Vagrant ada tiga layanan yang mungkin berguna:

- [Rove][rove]: layanan yang memungkinkan Anda untuk membangun mesin virtual Vagrant dengan bantuan Chef.
- [Puphpet][puphpet]: GUI sederhana untuk mengatur mesin virtual untuk pengembangan PHP. Selain
  VMs lokal, dapat digunakan untuk menyebarkan layanan _cloud_ juga. _Provisi_ ini dibuat dengan Puppet.
- [Protobox][protobox]: adalah _layer_ di atas vagrant dan GUI web untuk setup mesin virtual untuk pengembangan web. Sebuah dokumen YAML tunggal mengendalikan semuanya yang diinstal pada mesin virtual.

[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
[rove]: http://rove.io/
[puphpet]: https://puphpet.com/
[protobox]: http://getprotobox.com/
