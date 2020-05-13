# list-app
<!--Belajar membuat aplikasi web di progate menggunakn node.js, paket express dan paket ejs-->

<!-- 1. Yang Perlu Kamu Lakukan
    Komputer yang sudah diinstal Node.js
    Buat folder bernama "list-app" di mana saja di komputer kamu.
    Lalu buka folder ini di editor
    buka terminal dari path list-app
    contoh gambar di mac os
    https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/61/1581316824621.png -->

<!-- 2. Menjalankan Perintah dan Menginstal Paket
    Pertama, jalankan perintah berikut: -->
    npm init --yes

<!-- Ini adalah perintah yang digunakan untuk membuat package.json, yang merupakan file konfigurasi npm. Informasi pengaturan paket npm dijabarkan didalam file package.json. -->

<!-- Kemudian instal paket npm. Dalam artikel ini kita akan menginstal express dan ejs. Untuk melakukannya, jalankan perintah berikut: -->
    npm install express ejs

<!-- Jika kamu melihat gambar seperti di bawah ini, artinya instalasi sudah selesai. 
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/61/1581316879898.png -->

<!-- *Kamu bisa menjalankan setiap perintah npm install express dan npm install ejs, secara terpisah. Tapi dengan menulis npm intall Package1 Package2..., kamu akan bisa menginstal beberapa paket dengan satu perintah. -->

# Mulai dari Server dan Halaman Tampilan.
<!-- Pertama, siapkan file yang dibutuhkan. Buat file dan folder yang mengelilingi batas hijau, seperti gambar di bawah. Jika kamu berhasil mengikuti langkah sampai di sini, file lainnya akan dibuat.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/56/1578463105462.png
    a. buat folder yang dibutuhkan: folder views,(folder public(menyimpan css dan gambar)).
    b. buat file yang dibutuhkan: file app.js, (file hello.ejs => (berada didalam folder views)).
    c. Salin code di bawah ini dan tempelkan ke setiap file.-->

<!-- untuk file app.js-->
const express = require('express');

const app = express();

app.get('/', (req, res) => {
  res.render('hello.ejs');
});

app.listen(3000);

<!-- untuk file views/hello.ejs-->
<h1>Hello World</h1>

<!--Sekarang kamu telah selesai menyiapkan file. Mari coba memulai server.
di terminal ketik perintah:-->
node app.js
<!--Jika "Hello World" ditampilkan , kamu berhasil menyelesaikan langkah ini!-->

<!--Mohon diingat, kamu harus me-restart server setelah memodifikasi file js, agar perubahannya bisa diterapkan.
Kamu bisa me-restart server dengan mematikan, lalu memulai server lagi.
Untuk menerapkan perubahan dalam file, pertama-tama hentikan server dengan:-->
Ctrl + C
<!--lalu restart server dengan:-->
node app.js


# Membuat agar Server Restart Otomatis setelah Meng-update File
<!-- Kita sudah berhasil menampilkan halaman, tapi setiap ada perubahan di situ, kita harus me-restart server untuk menerapkannya.
Agar tidak me-restart server secara manual, mari instal nodemon, suatu paket npm yang dapat me-restart server secara otomatis saat ada perubahan dalam file. -->
npm install nodemon

<!-- jika berhasil akan tampil seperti ini
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/61/1581317006457.png -->

<!--Berikutnya, mari kita coba memulai server menggunakan nodemon. Untuk menjalankan nodemon, jalankan perintah berikut. (Kamu bisa salin lalu tempelkan perintah ini dengan Ctrl + V atau Ctrl + Shift + V).
Windows-->
.\\node_modules\\.bin\\nodemon app.js

<!-- Jika layar berikut ditampilkan, artinya kamu berhasil memulai server menggunakan nodemon.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/61/1581317022431.png -->


<!-- Ada Cara Mempermudah Proses Memulai nodemon
Menulis .\\node_modules\\.bin\\nodemon app.js setiap kali ingin menjalankan server terkesan agak repot. Mari kita pelajari cara agar proses ini jadi lebih mudah. -->

<!-- Buka file package.json di dalam "list-app." Kamu akan menemukan kolom bernama scripts di dalam file package.json.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/56/1578462759416.png -->

<!-- Kamu bisa mendaftarkan perintah yang sering digunakan sebagai tugas di dalam scripts, dan kamu dapat membukanya dengan mudah.
Mari coba mendaftarkan tugas.
Di sini kita akan menghapus tugas bernama test yang sudah ditulis dalam scripts, dan sebagai gantinya kita akan mendaftarkan tugas bernama start. Hapus baris `"test": 〜 dan masukkan perintah berikut.
Windows -->

 "start": ".\\node_modules\\.bin\\nodemon app.js"

 <!-- https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/56/157846276175.png -->

<!-- Mari jalankan tugas start yang baru kita daftarkan.
Syntax yang digunakan untuk ini adalah npm run taskname.
Jalankan perintah berikut dan periksa apakah kamu bisa memulai server menggunakan nodemon.-->
npm run start

<!-- https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/61/1581317086638.png -->
<!--Sekarang kamu bisa memulai server dengan cepat!-->

# Persiapan Local Environment MySQL(Windows)
<!--kamu akan mempelajari cara menginstal MySQL agar dapat digunakan dengan database di komputer kamu.-->
# 1. Persiapan untuk Instalasi
<!--buka Command Prompt  klik Run as administrator.
memeriksa apakah MySQL sudah diinstal.-->
mysql --version

<!--Jika ada versi yang ditampilkan, seperti mysql Ver 14.14 Distrib 5.7.28 for Win64 (x86_64), artinya MySQL sudah diinstal. Jika begitu, kamu bisa langsung melanjutkan ke artikel berikutnya.-->

# 2. Instalasi
<!--download mySQL pada url https://dev.mysql.com/downloads/windows/installer/5.7.html

langkah-langkah instal:
- pilih developer default
- pilih next dan execute pada check bawaan
- pilih standalone mySQL server, next next
- tetapkan password
- kosongkan centang pada start the mySQL server at startup,execute next next
- klik finish finish next
- masukkan password yg telah ditetapkan. saya pilih "root":Rinasamsi, execute finish finish
- kosongkan centang start mySQL workbench after setup dan start mySQL shell after setup.-->

# 3. Memeriksa Variable Environment
<!--Pada kotak pencarian di kiri bawah, ketik "environment variable." Ketika Edit the system environment variables ditampilkan, klik untuk membukanya.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/66/1582877617781.png
klik Path lalu Edit.
Di jendela baru yang membuka, kita akan mengubah area yang disorot pada gambar di bawah ini menjadi MySQL Server 5.7.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/66/1582877758879.png
 
Jika MySQL Server 5.7 sudah muncul, pindah ke bagian berikutnya, Uji Operasional MySQL.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/79/158554403810.png

Jalankan perintah berikut di Command Prompt untuk memeriksa bahwa environment variable sudah berubah.-->
mysql --version

<!--Jika versi seperti berikut ditampilkan mysql Ver 14.14 Distrib 5.7.28 for Win64 (x86_64), artinya langkah ini sudah selesai.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/66/1582608867914.png-->

# 4. Uji Operasional MySQL
<!--*Jika perintah ditolak dan tidak dapat dijalankan, ada kemungkinan kamu belum menjalankan Command Prompt sebagai administrator. Coba tutup aplikasi tersebut dan buka aplikasi lagi sebagai administrator.
Mulai MySQL terlebih dahulu agar dapat masuk. Pastikan agar langkah ini tidak terlupakan, karena tanpa melakukannya, kamu tidak akan bisa masuk.
Jika kamu berhasil memulai MySQL, The MySQL57 service was started successfully. akan ditampilkan. Namun, jika sudah dimulai, The requested service has already been started. akan ditampilkan.
Masuk
Setelah berhasil memulai MySQL, jalankan perintah berikut dan masuk sebagai root user.
*Seorang root user adalah pengguna Administrator yang memiliki akses ke semua perintah dan file.-->
mysql --user=root --password

<!--Setelah menjalankan perintah, Enter password: akan ditampilkan, jadi ketikkan kata sandi baru yang kamu gunakan sebelumnya lalu klik "Enter."
Jika berhasil masuk, kamu akan melihat layar seperti di bawah ini.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/66/1582608950112.png-->

<!--Keluar
Ayo kita coba keluar dari MySQL.-->
exit;
<!--Jika pesan Bye ditampilkan, artinya kamu sudah keluar.
Menghentikan MySQL
Terakhir, kita coba hentikan MySQL dengan menjalankan perintah berikut.-->
net stop mysql57

<!--The MySQL57 service was stopped successfully. akan ditampilkan jika kamu berhasil menghentikan MySQL.ika semua langkah berhasil diselesaikan, artinya environment MySQL sudah bekerja dan bisa langsung digunakan!-->

# Menghubungkan Aplikasi Node.js ke MySQL
<!-- Menyiapkan Aplikasi Dasar -->
<!-- Jika tidak memiliki aplikasi yang akan dihubungkan, buat aplikasi sederhana dengan mengikuti artikel Membuat Aplikasi Node.js Baru. -->
<!-- Menginstal Paket mysql
Pertama, instal Paket mysql. -->
npm install mysql

<!-- https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/64/1581318324681.png -->

# Membuat Database dan Tabel
<!-- Pilih data dan nama kolom pilihanmu sendiri. Untuk informasi tentang cara membuat database, baca artikel Membuat Database dengan MySQL.
Nama Database: list_app
Nama Tabel: users -->

# Memasuki Pengaturan mysql
<!-- Dalam app.js, kita akan mengimpor paket mysql dan menghubungkan ke MySQL dengan memasukkan informasi yang diperlukan seperti di bawah ini. Untuk passwordnya, gunakan password yang sama saat proses instalasi. -->

<!-- app.js -->
const express = require('express');
const mysql = require('mysql');

const app = express();

const connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: '[Password yang kamu gunakan sebelumnya]',
  database: 'list_app'
});

<!-- Selanjutnya, atur agar pesan kesalahan muncul saat tidak dapat terhubung ke MySQL. -->
<!-- app.js -->
connection.connect((err) => {
  if (err) {
    console.log('error connecting: ' + err.stack);
    return;
  }
  console.log('success');
});

<!-- Sekarang, tulis code yang membuat kita bisa mendapatkan dan menampilkan informasi dari MySQL. Dalam contoh ini, kita akan membuat detail database ditampilkan menggunakan console.log saat mengakses localhost:3000/. -->
<!-- app.js -->
app.get('/', (req, res) => {
  connection.query(
    'SELECT * FROM items',
    (error, results) => {
      console.log(results);
      res.render('hello.ejs');
    }
  );
});

app.listen(3000);

<!-- Jika app.js terlihat seperti gambar berikut, langkah ini sudah selesai.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/80/1585502653997.png -->

<!-- Terakhir, buat file tampilan yang akan ditampilkan dalam views/hello.ejs saat mengakses localhost:3000/. -->
<!-- views/hello.ejs -->
<h1>Hello World</h1>

<!-- Jika app.js sudah tersimpan, nyalakan server dengan menjalankan nodemon app.js, dan mengakses localhost:3000/.
Jika tampilan data di Terminal sudah sesuai dengan gambar di bawah ini, kamu sudah berhasil menyelesaikan langkah ini!
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/64/1581318369204.png -->

<!-- Mari kita uji untuk melihat apakah pesan kesalahan muncul ketika kita tidak dapat terhubung ke database. Coba ubah nama database seperti di bawah ini.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/64/1581318386541.png -->

<!-- Jika pesan kesalahan muncul seperti gambar di bawah, code untuk menentukan apakah aplikasi terhubung ke database sudah berfungsi dengan baik.
https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/64/1581318396467.png -->

<!-- Jangan lupa untuk mengubah informasi kembali ke aslinya. -->

