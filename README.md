# list-app
<!--Belajar membuat aplikasi web di progate menggunakn node.js, paket express dan paket ejs

1. Yang Perlu Kamu Lakukan
    Komuter yang sudah diinstal Node.js
    Buat folder bernama "list-app" di mana saja di komputer kamu.
    buka terminal dari path list-app

2. Menjalankan Perintah dan Menginstal Paket
    Pertama, jalankan perintah berikut:
    npm init --yes
    Ini adalah perintah yang digunakan untuk membuat package.json, yang merupakan file konfigurasi npm. Informasi pengaturan paket npm dijabarkan didalam file package.json.
    Kemudian instal paket npm. Dalam artikel ini kita akan menginstal express dan ejs. Untuk melakukannya, jalankan perintah berikut:
    npm install express ejs
    *Kamu bisa menjalankan setiap perintah npm install express dan npm install ejs, secara terpisah. Tapi dengan menulis npm intall Package1 Package2..., kamu akan bisa menginstal beberapa paket dengan satu perintah.

    Mari Mulai dari Server dan Halaman Tampilan.
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

<!--
3. Membuat agar Server Restart Otomatis setelah Meng-update File
    Kita sudah berhasil menampilkan halaman, tapi setiap ada perubahan di situ, kita harus me-restart server untuk menerapkannya.
    Agar tidak me-restart server secara manual, mari instal nodemon, suatu paket npm yang dapat me-restart server secara otomatis saat ada perubahan dalam file.-->
npm install nodemon

<!--Berikutnya, mari kita coba memulai server menggunakan nodemon. Untuk menjalankan nodemon, jalankan perintah berikut. (Kamu bisa salin lalu tempelkan perintah ini dengan Ctrl + V atau Ctrl + Shift + V).
Windows-->
.\\node_modules\\.bin\\nodemon app.js

<!--Jika layar [nodemon] starting node app.js ditampilkan, artinya kamu berhasil memulai server menggunakan nodemon.

Ada Cara Mempermudah Proses Memulai nodemon
Menulis .\\node_modules\\.bin\\nodemon app.js setiap kali ingin menjalankan server terkesan agak repot. Mari kita pelajari cara agar proses ini jadi lebih mudah.
Buka file package.json di dalam "list-app." Kamu akan menemukan kolom bernama scripts di dalam file package.json.

Kamu bisa mendaftarkan perintah yang sering digunakan sebagai tugas di dalam scripts, dan kamu dapat membukanya dengan mudah.
Mari coba mendaftarkan tugas.
Di sini kita akan menghapus tugas bernama test yang sudah ditulis dalam scripts, dan sebagai gantinya kita akan mendaftarkan tugas bernama start. Hapus baris `"test": 〜 dan masukkan perintah berikut.
Windows-->
 "start": ".\\node_modules\\.bin\\nodemon app.js"

<!-- Mari jalankan tugas start yang baru kita daftarkan.
Syntax yang digunakan untuk ini adalah npm run taskname.
Jalankan perintah berikut dan periksa apakah kamu bisa memulai server menggunakan nodemon.-->
npm run start

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
klik Path lalu Edit.
Di jendela baru yang membuka, kita akan mengubah area yang disorot pada gambar di bawah ini menjadi MySQL Server 5.7. Jika MySQL Server 5.7 sudah muncul, pindah ke bagian berikutnya, Uji Operasional MySQL.
Jalankan perintah berikut di Command Prompt untuk memeriksa bahwa environment variable sudah berubah.-->
mysql --version

<!--Jika versi seperti berikut ditampilkan mysql Ver 14.14 Distrib 5.7.28 for Win64 (x86_64), artinya langkah ini sudah selesai.-->

# 4. Uji Operasional MySQL
<!--*Jika perintah ditolak dan tidak dapat dijalankan, ada kemungkinan kamu belum menjalankan Command Prompt sebagai administrator. Coba tutup aplikasi tersebut dan buka aplikasi lagi sebagai administrator.
Mulai MySQL terlebih dahulu agar dapat masuk. Pastikan agar langkah ini tidak terlupakan, karena tanpa melakukannya, kamu tidak akan bisa masuk.
Jika kamu berhasil memulai MySQL, The MySQL57 service was started successfully. akan ditampilkan. Namun, jika sudah dimulai, The requested service has already been started. akan ditampilkan.
Masuk
Setelah berhasil memulai MySQL, jalankan perintah berikut dan masuk sebagai root user.
*Seorang root user adalah pengguna Administrator yang memiliki akses ke semua perintah dan file.-->
mysql --user=root --password

<!--Setelah menjalankan perintah, Enter password: akan ditampilkan, jadi ketikkan kata sandi baru yang kamu gunakan sebelumnya lalu klik "Enter."-->

<!--Keluar
Ayo kita coba keluar dari MySQL.-->
exit;
<!--Jika pesan Bye ditampilkan, artinya kamu sudah keluar.
Menghentikan MySQL
Terakhir, kita coba hentikan MySQL dengan menjalankan perintah berikut.-->
net stop mysql57

<!--The MySQL57 service was stopped successfully. akan ditampilkan jika kamu berhasil menghentikan MySQL.-->