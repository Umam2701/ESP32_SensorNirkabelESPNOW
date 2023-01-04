# Jaringan Sensor Nirkabel Menggunakan ESP-NOW

ESP-NOW adalah protokol yang dikembangkan oleh Espressif, yang memungkinkan banyak perangkat untuk berkomunikasi satu sama lain tanpa menggunakan Wi-Fi. Protokol ini mirip dengan konektivitas nirkabel 2.4GHz berdaya rendah. Pendifinisian alamat (MAC Address) pada masing-masing ESP32 diperlukan pada awal konfigurasi. Setelah konfigurasi alamat selesai dilakukan, jaringan peer-to-peer akan terbentuk dan perangkat tidak perlu melakukan handshaking kembali ketika akan berkomunikasi. Hal ini memunjukkan bahwa setelah perangkat ESP32 saling terpasang satu sama lain, koneksi akan tetap ada. Dengan kata lain, jika tiba-tiba salah satu ESP32 kehilangan daya atau diatur ulang, ketika restart, secara otomatis akan terhubung ke pasangan ESP32 yang telah terdefinisi alamatnya untuk melanjutkan komunikasi.


**Alat dan Bahan**
1) ESP32
2) Breadboard
3) Kabel jumper
4) Resistor 10K Ohm
<br>

**LANGKAH PERCOBAAN**

A. Memperoleh MAC Address ESP32 Receiver

![mencatat mac address](https://user-images.githubusercontent.com/118170084/210583064-66cb2368-ee35-4e3d-b0fd-6516b134113d.png)
<br>

B. ESP-NOW One-Way Point-to-Point Communication

`MAC Address Tx : 24:0A:C4:C6:06:54`

![mac tx 1](https://user-images.githubusercontent.com/118170084/210585845-12c2dcd7-a3ed-464c-b477-888e93f43a74.png)

![mac tx 2](https://user-images.githubusercontent.com/118170084/210585859-32f20871-0948-4609-9e65-397afd6cc0a6.png)

`MAC Address Rx : 30:AE:A4:7A:8F:B8`

![mac rx 1](https://user-images.githubusercontent.com/118170084/210586932-453cf26d-ec53-4740-b14e-9b834cfc1c0e.png)

![mac rx 2](https://user-images.githubusercontent.com/118170084/210586956-e41878ae-156c-4388-a985-0550a0784240.png)

![Capture1](https://user-images.githubusercontent.com/118172386/210174231-27c63ef7-d7b7-4f6f-9393-3fae47a03d06.JPG)

C. One-Way, One-to-Many Communication

a) Mengirim Pesan yang Sama Ke Beberapa Board ESP32
1. Siapkan 4 unit board ESP32.
2. Unggah program untuk mendapatkan Mac Address, kemudian catat masing-masing Mac Address pada setiap board ESP32 yang akan diatur sebagai Receiver.
3. Siapkan 1 unit ESP-32 yang akan dikonfigurasi sebagai Master/Sender.
4. Ketik program berikut ini dan tambahkan semua Mac Address ESP32 Receiver pada bagian broadcastAddress[].
5. Upload program tersebut pada board ESP32 Sender.
6. Siapkan board Receiver, kemudian ketik script berikut ini pada Arduino IDE.
7. Upload program tersebut pada Receiver.
8. Dokumentasikan output dari program tersebut secara lengkap pada masing-masing board.

MAC Address yang digunakan :

MAC Sender (Syauqi & Vania) : 3C:71:BF:F1:4B:08

MAC Reciver 1 (Noviantie & Dionysius) : 24:6F:28:02:C3:1C

MAC Receiver 2 (Hesti & Nabila) : 24:0A:C4:C6:06:54

MAC Receiver 3 (Cantika & Razan) : 30:AE:A4:7A:8F:B8

Pada Receiver 3, Hasilnya adalah sebagai berikut
![Picture6](https://user-images.githubusercontent.com/118172386/210175529-3e0865a4-bc50-463b-b6a0-61fedb48f0f6.png)

9. Matikan salah satu board Receiver, dokumentasikasikan hasilnya, dan buatlah analisisnya.

Pada Receiver 3, Hasilnya adalah sebagai berikut
![Picture7](https://user-images.githubusercontent.com/118172386/210175544-5621ba44-1a00-4639-8de3-751b6af1940e.png)

10. Buatlah koneksi menggunakan semua board ESP32 yang ada dikelas, dengan menambahkan Receiver ke dalam jaringan secara bertahap,
11. Dokumentasikan hasilnya secara lengkap. Catat dan analisis jumlah board maksimal yang dapat membentuk jaringan

b) Mengirim Pesan yang Berbeda Ke Beberapa Board ESP32
1. Siapkan 4 board ESP32, 1 board sebagai Sender dan 3 board sebagai Receiver.
2. Buatlah program pada Sender agar dapat mengirim pesan yang berbeda pada 3 Receiver.
3. Tips : Buat 3 buat struktur data.
Buat 3 random data dummy generator pada masing-masing variabel x dan y.
Gunakan fungsi esp_now_send() pada masing-masing broadcastAddress dengan
script yang terpisah

D. One-Way, Many-to-One Communication 

Di dalam mode ini, Receiver harus dapat mengidentifikasi setiap MAC Address unik dari Sender. Namun, untuk dapat membaca MAC Address yang berbeda cukup rumit dan butuh
sedikit trik. Sehingga, untuk membuatnya lebih mudah, masing-masing Sender akan diberikan ID unik, agar Receiver dapat lebih mudah mengidentifikasi Sender.
1. Siapkan 4 board ESP32. 3 board diatur sebagai Sender dan 1 board diatur sebagai Receiver.
2. Unggah program untuk menemukan MAC Address pada board Receiver, kemudian catat MAC Address-nya.

MAC Address ESP32 yang digunakan :

MAC Sender 1 (Syauqi & Vania) : 24:0A:C4:C5:E2:DC

MAC Sender 2 (Hesti & Nabila) : 24:0A:C4:C6:06:54

MAC Sender 3 (Cantika & Razan) : 24:0A:C4:C6:0E:7C

MAC Receiver  (Dionysius & Noviantie) : 3C:71:BF:F1:42:70

3. Ketikkan program berikut pada Arduino IDE untuk mengkonfigurasi board Sender
4. Upload program tersebut pada board Sender.
5. Siapkan board Receiver, ketikkan script berikut di Arduino IDE, kemudian upload program tersebut.
6. Buka serial monitor dan dokumentasikan output program.

Dari Pihak Sender akan muncul seperti dibawah
![Picture4](https://user-images.githubusercontent.com/118172386/210175087-c52e10d8-9700-4b07-861d-dec8f5ce6d2d.png)


Dari Pihak Receiver akan muncul seperti dibawah
![Picture5](https://user-images.githubusercontent.com/118172386/210175089-02992e20-cc69-4b7e-8910-5d10559d9cf1.png)

E. Two-Way Communication
1. Siapkan 2 unit ESP32 dan 2 unit sensor DHT11.
2. Buatlah rangkaian seperti pada Gambar di bawah ini.

![Capture](https://user-images.githubusercontent.com/118172386/210173864-32fef3ae-6fe2-4463-bbf7-10462a2a3d51.JPG)

3. Install library sensor DHT 11 melalui Sketch > Include Library > Manage Libraries. Ketikkan DHT pada kolom pencarian, pilih library yang akan diinstall seperti pada
Gambar berikut ini. Kemudian install juga Adafruit Unified Sensor menggunakan cara yang sama.
4. Upload program berikut ini untuk melakukan pengecekan sensor DHT11.
5. Dokumentasikan output program yang ditampilkan pada serial monitor Arduino IDE.
6. Unggah program menemukan MAC Address pada masing-masing board, kemudian catat MAC Address-nya.
7. Ketikkan script berikut, kemudian masukkan MAC Address receiver pada masingmasing board.
8. Upload program pada masing-masing board.
9. Buka serial monitor pada Arduino IDE, kemudian dokumentasikan outputnya.
10. Buatlah jaringan sensor nirkabel ESPNow topologi MESH berlandaskan Two-Way Communication. Diagram blok jaringan dapat dilihat pada Gambar 5.

Bentuk Rangkaian

![Picture2](https://user-images.githubusercontent.com/118172386/210173997-db16f6c3-43fd-41d2-8d5c-6e4d15aede02.png)


Tampilan pada Serial Monitor

![Picture3](https://user-images.githubusercontent.com/118172386/210173992-b4dfa271-443d-4b5d-95d1-972995517a3b.png)

