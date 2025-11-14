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
> [!NOTE]
> Jika pada folder musik belum ada musik sama sekali, maka tambahkan musik terlebih dahulu.

### 1.4 Setup Bind to Address
Langkah selanjutnya adalah mengubah ```bind_to_address```. Lakukan pencarian cepat seperti sebelumnya, kemudian ubah```bind_to_address``` menjadi:
```
bind_to_address    "0.0.0.0"
```
> [!NOTE]
> Jika masih ada tanda ```#```, hapus terlebih dahulu.

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

> [!NOTE]
> Agar MPD otomatis jalan saat komputer boot, masukkan Sytax berikut:
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
sudo pacman -S mpc
```
**B. Instalasi M.A.L.P**

Untuk MPD Client menggunakan M.A.L.P hanya khusus perangkat seperti handphone. Cara installnya juga cukup mudah, anda hanya perlu masuk ke ```Play Store``` dan ketik ```M.A.L.P``` kemudian unduh.

> [!NOTE]
> Sebelum lanjut, penting untuk cek IP dengan ketik di terminal
>```hostname -I```
> dan cek port dengan ketik ```sudo nano /etc/mpd.conf``` di terminal dan cari portnya dengan mudah dengan cara <kbd>Ctrl</kbd> + <kbd>W</kbd> lalu cari "port", di situ akan muncul berapa port yang anda pakai

### 2.2 Konfigurasi MPC
Setelah instal MPC lewat terminal, export IP yang tertera, jika di Arch, gunakan (contoh)
```
export MPD_HOST=172.19.162.32
```
Portnya:
```
export MPD_PORT=6600
```

### 2.3 Konfigurasi M.A.L.P
Setelah download M.A.L.P di Play Store, klik garis 3 ☰ di atas kiri dan klik *Profiles* di kolum *Settings*, lalu klik tombol + di atas kanan.

<img width="422" height="57" alt="Screenshot_779" src="https://github.com/user-attachments/assets/c9dfba85-6be0-4497-98a1-f7ded371fc10" />

**Tombol ☰, Profiles dan tombol +**

Jika sudah, kalian akan ditujukan ke *Edit profile*, di sana kalian harus masukkan: *Profile name*, *hostname atau IP*, *port*, dan yang terakhir aktifkan *Enable streaming from server* yang berisi link dari MPD, jika sudah save 

<img width="417" height="553" alt="Screenshot_780" src="https://github.com/user-attachments/assets/45ae69c6-6e49-4d81-9d10-76cedf2d7acf" />

**Image edit profile M.A.L.P**

## 3. Testing dan Penggunaan

### 3.1 Testing dengan MPC
Jika sudah instalasi dan konfig IP dan port MPC, lagu bisa langsung didengarkan dengan command
```
mpc play
```
Lalu pergi dengan URL IP dan Port, yaitu (jika mengikuti contoh):
https://172.19.162.32:8000
> [!NOTE]
> Port 6600 untuk MPD Control Protocol dan
> Port 8000 untuk HTTP Audio Stream

Jika ingin tau lagu apa yang sedang diputar, jalankan command
```
mpc status
```

![mpd 4](https://github.com/user-attachments/assets/6520571d-7efc-425d-8533-a5dcde168eb2)
<div align="center">

**Image bukti testing MPC**

</div>

### 3.2 Testing dengan M.A.L.P
Ketika semua step di bagian 2.3 sudah dijalankan seperti pemasangan IP, port, dan URL, pergi ke website dengan URL yang sudah kalian letakkan di *Streaming URL* dan lagu siap didengarkan

<img width="413" height="561" alt="Screenshot_781" src="https://github.com/user-attachments/assets/b38d6075-1074-4742-a131-5eb085b782c9" />

**Bukti M.A.L.P berhasil**

# 4. Topologi Client Server MPD
## 4.1 Image Topologi

![diagram (2)](https://github.com/user-attachments/assets/8ae267a0-1b36-45cc-baa5-b92601107767)
<div align="center">

**Image topologi server ke client** 

</div>

## 4.2 Penjelasan Topologi

### Konfigurasi Jaringan

| Komponen | Detail |
|-----------|---------|
| **Network Range** | 192.168.43.0/24 |
| **Gateway** | 192.168.43.1 |
| **Server IP** | 192.168.43.176 |
| **Hostname** | mpd |
| **OS** | Debian |

### Services & Ports

| Service | Port | Fungsi |
|---------|------|---------|
| **MPD Protocol** | 6600 | Kontrol dan komunikasi client |
| **HTTP Stream** | 8000 | Streaming audio (Ogg Vorbis) |

**Firewall**: UFW dengan port 6600 dan 8000 dibuka untuk akses LAN.

### Lokasi Data

```
Music Library : /home/bagas/Music/
MPD Database  : /home/bagas/.mpd/tag_cache
Audio Output  : ALSA (Speaker laptop)
Stream Format : Vorbis 44.1kHz 16-bit Stereo
```

### Akses Client

**1. Local Client (Mesin yang Sama)**
- Koneksi: `localhost:6600`
- Client: mpc / ncmpcpp

**2. Remote Clients (LAN)**
- Koneksi: `192.168.43.176:6600` (MPD protocol)
- Koneksi: `http://192.168.43.176:8000` (HTTP stream)
- Client: mpc (laptop teman), M.A.L.P (smartphone teman)

### Alur Koneksi

```
Download MP3 → /home/bagas/Music/ → Update MPD Database
                                   ↓
Client (6600) → MPD Server → ALSA Output → Speaker
Client (8000) → HTTP Stream → Vorbis Audio
```

### Penggunaan

Server ini digunakan untuk berbagi musik dengan teman dalam satu jaringan lokal. Semua client dapat mengontrol playback yang sama dan mendengarkan audio secara realtime melalui HTTP stream atau langsung dari speaker laptop server.

**Catatan**: Setup ini hanya untuk jaringan lokal

#### Bukti Instalasi MPD Server
<img width="1366" height="768" alt="MPD Server" src="https://github.com/user-attachments/assets/908f501e-b710-4d3c-9fec-6f34b8c645e6" />
