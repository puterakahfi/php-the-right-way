---
isChild: true
anchor: containers
---

## Containers {#containers_title}

Hal pertama yang harus Anda mengerti tentang Dependency Injection Wadah adalah bahwa mereka tidak sama dengan Dependency
Injection. Sebuah wadah adalah utilitas kenyamanan yang membantu kita menerapkan Dependency Injection, bagaimanapun, mereka dapat dan sering
disalahgunakan untuk menerapkan anti-pola, Layanan Lokasi. Penyuntikan wadah DI sebagai Layanan Locator ke kelas Anda dibilang
menciptakan ketergantungan keras pada wadah dari ketergantungan yang akan diganti. Hal ini juga membuat kode Anda jauh lebih transparan
dan akhirnya sulit untuk menguji.

Kebanyakan kerangka modern memiliki Dependency Injection Kontainer mereka sendiri yang memungkinkan Anda untuk kawat dependensi Anda bersama-sama melalui konfigurasi.
Apa ini berarti dalam prakteknya adalah bahwa Anda dapat menulis kode aplikasi yang bersih dan de-digabungkan sebagai kerangka itu dibangun di atas.
