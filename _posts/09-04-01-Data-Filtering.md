---
isChild: true
anchor: data_filtering
---

## Data Filtering {#data_filtering_title}

Tidak pernah ( pernah) kepercayaan masukan asing diperkenalkan ke kode PHP Anda . Selalu membersihkan dan memvalidasi
masukan asing sebelum menggunakannya dalam kode . The ` filter_var ` dan ` filter_input ` fungsi dapat membersihkan teks dan memvalidasi format teks ( misalnya
alamat email ) .

Masukan asing bisa apa saja : ` $ _GET ` dan ` $ _POST ` input data form, beberapa nilai dalam ` $ _SERVER `
superglobal , dan HTTP request tubuh melalui ` fopen ( ' php :/ / input' , ' r ' ) ` . Ingat , masukan asing tidak
terbatas untuk membentuk data yang diajukan oleh pengguna . Upload dan download file , nilai session , data cookie ,
dan data dari layanan web pihak ketiga adalah input asing , juga.

Sedangkan data asing dapat disimpan , dikombinasikan , dan diakses kemudian, masih masukan asing . setiap
kali Anda memproses , output, menggabungkan , atau menyertakan data dalam kode Anda , tanyakan pada diri Anda apakah
Data disaring dengan baik dan hal itu dapat dipercaya .

Data dapat _filtered_ berbeda berdasarkan tujuannya . Misalnya, ketika masukan asing tanpa filter dilewatkan
menjadi output halaman HTML , dapat mengeksekusi HTML dan JavaScript di situs Anda! Hal ini dikenal sebagai Cross- Site
Scripting ( XSS ) dan bisa menjadi serangan yang sangat berbahaya . Salah satu cara untuk menghindari XSS adalah untuk membersihkan semua user-generated
data sebelum keluaran ke halaman Anda dengan menghapus tag HTML dengan ` ` strip_tags fungsi atau melarikan diri
karakter dengan makna khusus menjadi entitas HTML masing-masing dengan ` htmlentities `
atau ` fungsi htmlspecialchars ` .

Contoh lain adalah lewat opsi akan dieksekusi pada baris perintah . Ini bisa sangat berbahaya
( dan biasanya ide yang buruk ) , tetapi Anda dapat menggunakan built -in ` escapeshellarg ` berfungsi untuk membersihkan dieksekusi
argumen perintah itu .

Salah satu contoh terakhir adalah menerima masukan asing untuk menentukan file untuk memuat dari filesystem . Hal ini dapat dimanfaatkan oleh
mengubah nama file ke path file . Anda harus menghapus " / " , " .. / " , [ nol byte ] [ 6 ] , atau karakter lain dari path file sehingga tidak bisa
memuat file tersembunyi , non - publik , atau sensitif .

* [Pelajari tentang data filtering][1]
* [Pelajari tentang `filter_var`][4]
* [Pelajari tentang `filter_input`][5]
* [Pelajari tentang handling null bytes][6]

### Sanitization

Menghapus Sanitasi (atau lolos) ilegal atau tidak aman karakter dari input asing.

Misalnya, Anda harus membersihkan masukan asing sebelum termasuk input dalam HTML atau memasukkan itu
menjadi query SQL mentah. Bila Anda menggunakan parameter terikat dengan [PDO] (# database), maka akan
membersihkan masukan untuk Anda.

Kadang-kadang diperlukan untuk memungkinkan beberapa tag HTML aman di input ketika termasuk dalam HTML
halaman. Hal ini sangat sulit untuk dilakukan dan banyak menghindarinya dengan menggunakan format lebih terbatas lainnya seperti
Penurunan harga atau BBCode, meskipun membolehkan akses perpustakaan seperti [HTML Purifier] [html-pembersih] ada untuk
alasan ini.

[Lihat Sanitization Filters][2]

### Validation

Validasi memastikan bahwa masukan asing adalah apa yang Anda harapkan. Sebagai contoh, Anda mungkin ingin untuk memvalidasi
alamat email, nomor telepon, atau usia saat memproses pengajuan pendaftaran.

[Lihat Validation Filters][3]

[1]: http://www.php.net/manual/en/book.filter.php
[2]: http://www.php.net/manual/en/filter.filters.sanitize.php
[3]: http://www.php.net/manual/en/filter.filters.validate.php
[4]: http://php.net/manual/en/function.filter-var.php
[5]: http://www.php.net/manual/en/function.filter-input.php
[6]: http://php.net/manual/en/security.filesystem.nullbytes.php
[html-purifier]: http://htmlpurifier.org/
