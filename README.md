# Sistem Absensi Terintegrasi

<p align="center"><a href="" target="_blank"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSqZ4zUJYtla6UURcmT91UEB0_s0JOXsPWFrUjBloBEVA&s" width="20%" alt="Watumas Logo"></a></p>
<p align="center">
</p>

## Deskripsi
Sistem Absensi Klinik Watumas adalah sebuah sistem yang dikembangkan untuk kepentingan absensi karyawan di klinik watumas purwokerto. Sistem ini dikembangkan dengan mengintegrasikan 3 (tiga) stack teknologi, yaitu **IoT, Web, dan Mobile App.** Selain itu, sistem ini juga bertujuan agar adanya Transparansi yang jelas terkait pencatatan Absensi Karyawan, mulai dari Jam Masuk, Jam Keluar, Keterlambatan, Jumlah Jam Kerja, Absensi Izin/Sakit, Hingga Statistik absensi karyawan tiap bulannya. berikut adalah gambaran bagaimana setiap stack teknologi pada sistem absensi ini saling terintegrasi: 

<p align="center"><a href="" target="_blank"><img src="https://github.com/Klinik-Watumas/Overview/blob/main/assets/Group%2039.png" width="100%" alt="Watumas Project"></a></p>
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

