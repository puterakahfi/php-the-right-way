---
anchor: dependency_management
---

# Dependency Management {#dependency_management_title}

Ada ton perpustakaan PHP, kerangka kerja, dan komponen untuk memilih dari. Proyek Anda mungkin akan menggunakan beberapa dari mereka - ini adalah dependensi proyek. Sampai saat ini, PHP tidak memiliki cara yang baik untuk mengelola dependensi proyek ini. Bahkan jika Anda berhasil secara manual, Anda masih harus khawatir tentang autoloaders. Tidak ada lagi.

Saat ini ada dua sistem manajemen paket utama untuk PHP - Komposer dan PEAR. Mana yang tepat bagi Anda? Jawabannya adalah keduanya.

 * Gunakan **Composer** ketika mengelola dependensi untuk satu proyek.
 * Gunakan **PEAR** ketika mengelola dependensi untuk PHP secara keseluruhan pada sistem Anda.

Secara umum, paket Composer akan tersedia hanya dalam proyek-proyek yang secara eksplisit Anda tentukan sedangkan paket PEAR akan tersedia bagi semua proyek PHP Anda. Sementara PEAR mungkin terdengar seperti lebih mudah pendekatan pada pandangan pertama, ada keuntungan untuk menggunakan proyek-by-proyek pendekatan dependensi Anda.
