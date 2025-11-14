# Panduan Instalasi MPD Client-Server di Debian Linux
Sebelum melakukan instalasi MPD Client-Server, masuk ke dalam terminal Linux Debian dan ketik Syntax berikut. Lalu masukkan password linux anda:
```
sudo apt update
```
## 1. Setup MPD Server

### 1.1 Instalasi MPD
Install MPD Server menggunakan Syntax berikut:
```
sudo apt install mpd -y
```
### 1.2 Konfigurasi MPD Server
Kemudian Konfigurasi MPD Server menggunakan Syntax berikut:
```
sudo nano /etc/mpd.conf
```
### 1.3 Setup Direktori Musik
Setelah masuk ke dalam nano MPD langkah selanjutnya adalah mencari dan mengedit ```music_directory```. Cara cepatnya adalah masuk ke menu pencarian nano MPD dengan menekan ```CTRL + W``` lalu ketik ```music_directory```, dan tekan ```Enter```. Selanjutnya ganti Path sesuai dengan folder musik yang ada pada Linux Debian anda. Misal path yang awanya seperti ini:
```
music_directory    "/var/lib/mpd/music"
```
Diubah menjadi seperti berikut:
```
music_directory    "/home/bagas/Music"
```
*Note: Jika pada folder musik belum ada musik sama sekali, maka tambahkan musik terlebih dahulu.*

### 1.4 Setup Bind to Address
Langkah selanjutnya adalah mengubah ```bind_to_address```. Lakukan pencarian cepat seperti sebelumnya, kemudian ubah```bind_to_address``` menjadi:
```
bind_to_address    "0.0.0.0"
```
*Note: Jika masih ada tanda ```#```, hapus terlebih dahulu.*

### 1.5 Tambahkan HTTP Stream
Scroll pada konfigurasi nano MPD Server sampai dibagian paling bawah. Cara cepatnya dengan menekan ```CTRL + End```, lalu tambahkan Syntax berikut:
```
audio_output {
    type		"httpd"
    name		"HTTP Stream"
    encoder		"vorbis"
    port		"8000"
    bind_to_address	"0.0.0.0"
    quality		"5.0"
    format		"44100:16:2"
}
```

### 1.6 Simpan Konfigurasi MPD Server
Sebelum keluar dari konfigurasi nano MPD Server, tekan ```CTRL + O``` kemudian tekan lagi ```Enter``` untuk menyimpan konfigurasi yang telah dibuat. Selanjutnya tekan ```CTRL + X``` untuk keluar dari konfigurasi nano MPD Server.

### 1.7 Verifikasi Instalasi MPD Server
Setelah melakukan konfigurasi, langkah selanjutnya adalah merestart MPD Server. Masukkan Syntax berikut:
```
sudo systemctl restart mpd
```
Kemudian cek status MPD dengan Syntax:
```
sudo systemctl status mpd
```
Jika sudah running dan tidak ada error, maka MPD Server sudah dapat dijalankan dengan baik!

**Tambahan: Agar MPD otomatis jalan saat komputer boot, masukkan Sytax berikut:**
```
sudo systemctl enable mpd
```

## 2. Setup Client MPD
Langkah selanjutnya adalah menginstall Client MPD, disini saya akan mencontohkan dengan 3 MPD Client berbeda yaitu: MPC, ncmpcpp, dan MILP.
### 2.1 Instalasi MPD Client
**Instalasi MPC**

**Instalasi ncmpcpp**

**Instalasi MILP**

### 2.2 Konfigurasi MPC

### 2.3 Konfigurasi ncmpcpp 

### 2.4 Konfigurasi MILP


## 3. Testing dan Penggunaan

### 3.1 Testing dengan MPC

### 3.2 Testing dengan ncmpcpp

### 3.3 Testing dengan MILP

### 3.4 Testing HTTP Streaming
