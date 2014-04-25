---
title: File Konfigurasi
isChild: true
anchor: configuration_files
---

## File Konfigurasi {#configuration_files_title}

Ketika membuat file konfigurasi untuk aplikasi Anda, praktik terbaik merekomendasikan bahwa salah satu metode berikut
harus diikuti:

- Dianjurkan agar Anda menyimpan informasi konfigurasi Anda di mana tidak dapat diakses secara langsung dan ditarik
melalui sistem file.
- Jika Anda harus menyimpan file konfigurasi di root dokumen, nama file dengan ekstensi php ``.. ini
memastikan bahwa, bahkan jika script diakses secara langsung, itu tidak akan menjadi output sebagai teks biasa.
- Informasi dalam file konfigurasi harus dilindungi sesuai, baik melalui enkripsi atau file group / user
sistem perizinan
