# Sistem Absensi Terintegrasi

<p align="center"><a href="" target="_blank"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSqZ4zUJYtla6UURcmT91UEB0_s0JOXsPWFrUjBloBEVA&s" width="20%" alt="Watumas Logo"></a></p>
<p align="center">
</p>

## Deskripsi
Sistem Absensi Klinik Watumas adalah sebuah sistem yang dikembangkan untuk kepentingan absensi karyawan di klinik watumas purwokerto. Sistem ini dikembangkan dengan mengintegrasikan 3 (tiga) stack teknologi, yaitu **IoT, Web, dan Mobile App.** Selain itu, sistem ini juga bertujuan agar adanya Transparansi yang jelas terkait pencatatan Absensi Karyawan, mulai dari Jam Masuk, Jam Keluar, Keterlambatan, Jumlah Jam Kerja, Absensi Izin/Sakit, Hingga Statistik absensi karyawan tiap bulannya. berikut adalah gambaran bagaimana setiap stack teknologi pada sistem absensi ini saling terintegrasi: 

<p align="center"><a href="" target="_blank"><img src="/ovrvw.png" width="80%" alt="Watumas Project"></a></p>
<p align="center">
</p>

# Project-Overview
Seperti yang telah dikatakan sebelumnya, sistem absensi ini menggabungkan antara 3 stack teknologi yaitu:
- IoT
- Web
- Mobile App

Berikut adalah Penjelasan dari masing masing stack teknologi tersebut:

## IoT *(Internet of Things)*
Internet of Things adalah sebuah konsep yang terhubung dengan perangkat sebagai media komunikasi berbasis internet. Dengan adanya IoT, seorang user dapat saling terhubung dan berkomunikasi untuk melakukan aktivitas tertentu, mencari, mengolah, dan mengirimkan informasi secara otomatis.

Dalam hal ini IoT akan berperan sebagai alat yang menerima input dari *User* dan mengirimkannya ke Server sebagai data Absensi,
Alat-alat atau Hardware yang digunakan pada IoT ini adalah sebagai berikut:
- **RFID Card**
- **RFID Sensor**
- **ESP8266**
- **OLED LCD Display**

RFID Card Berperan sebagai identitas atau akun untuk setiap *User atau Karyawan*,
RFID Sensor sendiri berperan menjadi perangkat Input bagi IoT ini yang menerima inputan dari *User* melalui RFID Card masing masing *User*
ESP8266 Berperan menjadi otak yang mengatur segala input output dan pengolahan data
Terakhir, OLED LCD Display akan berperan menjadi perangkat output yang akan menampilkan hasil dari pemrosesan yang dilakukan oleh ESP8266

### Alur Kerja *(Work Flow)* IoT
1. Setiap Karyawan memiliki RFID Card mereka masing masing yang akan digunakan untuk melakukan Absensi.
2. Absensi dilakukan dengan cara mendekatkan/menempelkan RFID Card ke RFID Sensor
3. RFID Sensor akan mendeteksi adanya RFID Card dan mengirimkan data RFID Card tersebut ke ESP8266
4. Saat ESP8266 menerima inputan dari RFID Sensor, ddata tersebut akan diproses, Proses yang dilakukan oleh ESP8266 antara lain adalah:
    - Menerima data RFID Card
    - Mengambil data `waktu dan tanggal` saat ini pada waktu inputan diterima
    - mengirimkan data `waktu` `tanggal` dan `data RFID` ke Server melalui API
    - menerima Response dari Server
    - mengelola response server dan mengirimkannya ke OLED LCD Display untuk ditampilkan
5. OLED LCD Display akan menampilkan Pesan/Teks yang dikirim oleh ESP8266

### Detail IoT
<img src="/wire.png" width="50%" alt="IoT Detail">


## Web
Dalam sistem Absensi Terintegrasi Klinik Watumas, Website akan berperan sebagai pusat utama dalam pengumpulan dan pengolahan data.
Website dibangun dengan menggunakan bahasa pemrograman PHP dengan framework `Laravel Versi 11`

<img src="/landing.png" width="80%" alt="Landing Page">

Integrasi dengan IoT dan Mobile App dilakukan dengan menggunakan API yang dibuat pada website ini. Jadi, antara IoT, Web dan Mobile App akan dapat saling terhubung secara *realtime* dengan komunikasi menggunakan API ini. API yang dibuat antara lain
#### IoT
- `Attendances API`
    dengan API ini, Absensi karyawan dapat dibuat menggunakan perangkat IoT yang terhubung dengan API *Create Attendances*
#### Mobile App
- `Auth API`
    Melakukan Login
- `Get Company API`
    Mengambil Nama, Foto, dan Lokasi Klinik Watumas
- `Come Attendances API`
    Membuat Absen Kehadiran Karyawan
- `Home Attendances API`
    Membuat Absen Kepulangan Karyawan
- `Absent Attendances API`
    Membuat Absen Ketidak Hadiran Karyawan
- `Get Today Attendances API`
    Mengambil data Absensi Karyawan hari ini
- `Get Statistic Attendances API`
    Mengambil data Statistik Absensi Karyawan Pada Bulan tertentu
- `Get Details Attendances API`
    Mengambil semua detail absensi karyawan pada Bulan tertentu
- `Get User Profile API`
    Mengambil data Akun Karyawan seperti Nama, Email dan Foto Profil
- `Update User Profile API`
    Memperbarui data Akun Karyawan


Selain itu, website akan berperan sebagai *Company Profile* Klinik Watumas, dan *Admin Dashboard* yang digunakan sebgai:
- Pemantauan data Absensi Karyawan
- Melakukan Rekapitulasi data Absensi
- Konfigurasi Sistem Absensi
- Pengaturan Akun dan RFID Karyawan
- Melakukan Absensi untuk Karyawan yang mengalami kendala
- Manajemen Konten pada Halaman Company Profile Klinik Watumas
- Manajemen Notifikasi Aplikasi Mobile
- Pemantauan Log Aktifitas Admin

<img src="/webapp.png" width="80%" alt="Web Detail">

**Catatan:** API Mobile Attendances untuk membuat absensi keberangkatan dan kepulangan hanya dapat dilakukan jika Admin **Mengaktifkan Konfigurasi `Mobile App Attendances`**, karena pada sistem Absensi terintegrasi ini fokus utama untuk melakukan absen kedatangan dan kepulangan menggunakan IoT

## Mobile App
Aplikasi Mobile Sistem Absensi Klinik Watumas adalah sebuah Aplikasi Berbasis Android yang dapat diinstall oleh setiap Karyawan Klinik Watumas, Tujuan dan Fokus Utama pada Aplikasi Mobile ini adalah:
- Sebagai Pemantauan terhadap Data Absensi Masing Masing Karyawan
- Sebagai Backup atau Cadangan jika terjadi sesuatu pada Perangkat IoT sehingga tidak dapat melakukan Absensi Kedatangan dan Kepulangan
- Sebagai Sistem/Alat untuk melakukan Absensi Ketidak Hadiran Karyawan

<img src="/mobile.png" width="80%" alt="Mobile App">

### Fitur Fitur pada Mobile App
- Login
- Membuat Absen Kehadiran`**`
- Membuat Absen Kepulangan`**`
- Membuat Absen Ketidak Hadiran
- Melihat Data Absensi Hari Ini
- Melihat Statistik Absensi pada Bulan Tertentu
- Melihat Detail Absensi pada Bulann Tertentu
- Melakukan Pembaruan Profil Pengguna (nama pengguna dan foto profil)
- Melakukan Pembaruan Password Akun Pengguna

**Catatan**: Tanda `**` menandakan fitur memerlukan izin dari Admin (Admin mengaktifkan konfigurasi `Mobile App Attendances` pada Web Admin)
