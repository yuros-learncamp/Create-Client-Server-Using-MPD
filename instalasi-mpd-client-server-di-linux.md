# Panduan Instalasi MPD Client-Server di Debian Linux
Sebelum melakukan instalasi MPD Client-Server, masuk ke dalam terminal Linux Debian dan ketik Syntax berikut. Lalu masukkan password linux anda:

```
sudo apt update
```

## 1. Setup MPD Client-Server

### 1.1 Instalasi MPD
Install MPD Client-Server menggunakan Syntax berikut:

```
sudo apt install mpd -y
```

### 1.2 Konfigurasi MPD Server
Kemudian Konfigurasi MPD Client-Server menggunakan Syntax berikut:

```
sudo nano /etc/mpd.conf
```

### 1.3 Setup Direktori Musik
Setelah masuk kedalam nano MPD langkah selanjutnya adalah mencari dan mengedit music_directory. Ganti Pathnya sesuai dengan folder musik yang ada pada Linux Debian anda. Misal path yang awanya seperti ini:

```
music_directory    "/var/lib/mpd/music"
```

Diubah menjadi:
```
music_directory    "/home/bagas/Music"
```

### 1.4 Manajemen Service MPD

### 1.5 Konfigurasi Firewall

### 1.6 Verifikasi Instalasi Server


## 2. Setup Client MPD

### 2.1 Instalasi Client

### 2.2 Konfigurasi MPC Client

### 2.3 Konfigurasi ncmpcpp Client

### 2.4 Konfigurasi MILP Client


## 3. Testing dan Penggunaan

### 3.1 Testing dengan MPC

### 3.2 Testing dengan ncmpcpp

### 3.3 Testing dengan MILP

### 3.4 Testing HTTP Streaming
