# Jaringan Sensor Nirkabel Menggunakan ESP-NOW

ESP-NOW adalah protokol yang dikembangkan oleh Espressif, yang memungkinkan banyak perangkat untuk berkomunikasi satu sama lain tanpa menggunakan Wi-Fi. Protokol ini mirip dengan konektivitas nirkabel 2.4GHz berdaya rendah. Pendifinisian alamat (MAC Address) pada masing-masing ESP32 diperlukan pada awal konfigurasi. Setelah konfigurasi alamat selesai dilakukan, jaringan peer-to-peer akan terbentuk dan perangkat tidak perlu melakukan handshaking kembali ketika akan berkomunikasi. Hal ini memunjukkan bahwa setelah perangkat ESP32 saling terpasang satu sama lain, koneksi akan tetap ada. Dengan kata lain, jika tiba-tiba salah satu ESP32 kehilangan daya atau diatur ulang, ketika restart, secara otomatis akan terhubung ke pasangan ESP32 yang telah terdefinisi alamatnya untuk melanjutkan komunikasi.


**ALAT & BAHAN**
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

<img width="370" alt="data packet loss" src="https://user-images.githubusercontent.com/118170084/210589135-cb10126f-943e-461d-88d4-31818dce99bb.png">

C. One-Way, One-to-Many Communication

*a) Mengirim Pesan yang Sama Ke Beberapa Board ESP32*
MAC Address yang digunakan:

`MAC Sender : 3C:71:BF:F1:4B:08`

`MAC Reciver 1 : 24:6F:28:02:C3:1C`

`MAC Receiver 2 : 24:0A:C4:C6:06:54`

`MAC Receiver 3 : 30:AE:A4:7A:8F:B8`

Pada Receiver 3, Hasilnya adalah sebagai berikut.
![Picture6](https://user-images.githubusercontent.com/118172386/210175529-3e0865a4-bc50-463b-b6a0-61fedb48f0f6.png)

Pada Receiver 3 saat dimatikan board receiver, Hasilnya adalah sebagai berikut.
![Picture7](https://user-images.githubusercontent.com/118172386/210175544-5621ba44-1a00-4639-8de3-751b6af1940e.png)


D. One-Way, Many-to-One Communication 

MAC Address ESP32 yang digunakan :

`MAC Sender 1 : 24:0A:C4:C5:E2:DC`

`MAC Sender 2 : 24:0A:C4:C6:06:54`

`MAC Sender 3 : 24:0A:C4:C6:0E:7C`

`MAC Receiver  : 3C:71:BF:F1:42:70`

Dari Pihak Sender akan muncul seperti dibawah.
![Picture4](https://user-images.githubusercontent.com/118172386/210175087-c52e10d8-9700-4b07-861d-dec8f5ce6d2d.png)

Dari Pihak Receiver akan muncul seperti dibawah.
![Picture5](https://user-images.githubusercontent.com/118172386/210175089-02992e20-cc69-4b7e-8910-5d10559d9cf1.png)

E. Two-Way Communication

![Capture](https://user-images.githubusercontent.com/118172386/210173864-32fef3ae-6fe2-4463-bbf7-10462a2a3d51.JPG)

*Bentuk Rangkaian*

![Picture2](https://user-images.githubusercontent.com/118172386/210173997-db16f6c3-43fd-41d2-8d5c-6e4d15aede02.png)

*Tampilan pada Serial Monitor*

![Picture3](https://user-images.githubusercontent.com/118172386/210173992-b4dfa271-443d-4b5d-95d1-972995517a3b.png)

