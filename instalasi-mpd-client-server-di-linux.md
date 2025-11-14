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
Langkah selanjutnya adalah menginstall Client MPD, disini saya akan mencontohkan dengan 2 MPD Client berbeda yaitu: MPC, dan M.A.L.P.
### 2.1 Instalasi MPD Client
**A. Instalasi MPC**

Buka linux Debian pada perangkat desktop atau laptop lain, kemudian masuk ke dalam terminal. Setelah itu masukkan password linuxnya dan ketik Syntax berikut:
```
sudo apt install mpc -y
```
Untuk Linux Arch menggunakan Syntax:
```

```

**B. Instalasi M.A.L.P**

Untuk MPD Client menggunakan M.A.L.P hanya khusus perangkat seperti handphone. Cara installnya juga cukup mudah, anda hanya perlu masuk ke ```Play Store``` dan ketik ```M.A.L.P``` kemudian unduh.

### 2.2 Konfigurasi MPC

### 2.4 Konfigurasi M.A.L.P


## 3. Testing dan Penggunaan

### 3.1 Testing dengan MPC

### 3.2 Testing dengan M.A.L.P


# 4. Topologi Client Server MPD

# 5. Dokumentasi
## 5.1 Dokumentasi Install MPD Server
<img width="1366" height="768" alt="MPD Server" src="https://github.com/user-attachments/assets/908f501e-b710-4d3c-9fec-6f34b8c645e6" />

## 5.2 Dokumentasi MPC Client Server

## 5.3 Dokumentasi M.A.L.P Client Server
