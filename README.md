# ☆ DORAEMON STORE ROBLOX

<p align="center">
  <img src="assets/doraemon.gif" width="180" alt="Doraemon Store">
</p>

<h3 align="center">☆ WhatsApp Bot Top Up Robux ☆</h3>

<p align="center">
  Bot WhatsApp untuk mengelola penjualan Robux secara otomatis.
  <br>
  Mendukung order, QRIS, verifikasi pembayaran, status pesanan,
  management harga, broadcast, dan maintenance mode.
</p>

<p align="center">

![Node.js](https://img.shields.io/badge/Node.js-20%2B-339933?style=for-the-badge\&logo=node.js\&logoColor=white)
![WhatsApp](https://img.shields.io/badge/WhatsApp-Bot-25D366?style=for-the-badge\&logo=whatsapp\&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-Database-003B57?style=for-the-badge\&logo=sqlite\&logoColor=white)
![Termux](https://img.shields.io/badge/Termux-Supported-black?style=for-the-badge)

</p>

---

## ☆ Tentang

**DORAEMON STORE ROBLOX** adalah bot WhatsApp berbasis Node.js yang dirancang untuk membantu otomatisasi toko Robux.

Customer dapat melakukan proses pembelian langsung melalui WhatsApp tanpa harus menggunakan website tambahan.

### ☆ Fitur

* ☆ Menu otomatis
* ☆ Daftar harga Robux
* ☆ Sistem order
* ☆ Input username Roblox
* ☆ QRIS payment
* ☆ Pengiriman QRIS otomatis
* ☆ Upload bukti pembayaran
* ☆ Forward bukti pembayaran ke admin
* ☆ Verifikasi pembayaran
* ☆ Reject pembayaran
* ☆ Status order
* ☆ Management harga
* ☆ Maintenance mode
* ☆ Broadcast customer
* ☆ Database SQLite
* ☆ Session WhatsApp
* ☆ Auto timeout order
* ☆ Logging system
* ☆ Validasi input

---

# ☆ Preview

<p align="center">
  <img src="assets/doraemon.gif" width="500" alt="Doraemon Store Preview">
</p>

> Letakkan GIF preview di `assets/doraemon.gif`.

Jika tidak ingin menggunakan GIF, bagian ini dapat diganti dengan screenshot bot.

---

# ☆ Flow Pembelian

```text
┌──────────────────────┐
│      CUSTOMER        │
└──────────┬───────────┘
           │
           ▼
    ☆ Chat WhatsApp
           │
           ▼
        .menu
           │
           ▼
    ☆ Pilih Produk
           │
           ▼
 ☆ Masukkan Username Roblox
           │
           ▼
     ☆ Konfirmasi
           │
           ▼
     ☆ Buat Order
           │
           ▼
      ☆ QRIS Payment
           │
           ▼
    ☆ Kirim Bukti Bayar
           │
           ▼
    ☆ Admin Verifikasi
           │
      ┌────┴────┐
      ▼         ▼
    PAID      FAILED
      │         │
      ▼         ▼
 PROCESSING  CANCELLED
      │
      ▼
     DONE
```

---

# ☆ Persyaratan

Sebelum menjalankan project, pastikan sudah tersedia:

```text
Node.js >= 20
npm
Git
Python
Clang
Make
```

Project dapat dijalankan di:

```text
☆ Termux Android
☆ Linux
☆ VPS
```

---

# ☆ 1. Instalasi Node.js

## Linux / VPS

```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs git
```

Cek:

```bash
node -v
npm -v
```

---

## Termux Android

```bash
pkg update -y
pkg upgrade -y
pkg install nodejs-lts git python clang make -y
```

Cek:

```bash
node -v
npm -v
```

Minimal:

```text
Node.js 20+
```

---

# ☆ 2. Clone Project

```bash
git clone <url-repo-anda> doraemon-store
cd doraemon-store
```

Install dependency:

```bash
npm install
```

### Termux

`better-sqlite3` membutuhkan proses compile ketika instalasi.

Jika terjadi masalah:

```bash
pkg install python clang make -y
npm install
```

---

# ☆ 3. Konfigurasi `.env`

Copy:

```bash
cp .env.example .env
```

Edit:

```bash
nano .env
```

Contoh:

```env
ADMIN_WA=6281234567890
QRIS_IMAGE=assets/qris.jpg
```

---

# ☆ 4. Nomor Admin

Edit:

```env
ADMIN_WA=6281234567890
```

Gunakan format internasional tanpa `+`.

### Benar

```text
6281234567890
```

### Salah

```text
+6281234567890
081234567890
```

Nomor admin digunakan untuk:

```text
☆ Menerima notifikasi order
☆ Menerima bukti pembayaran
☆ Verifikasi pembayaran
☆ Management store
```

---

# ☆ 5. QRIS

QRIS default berada di:

```text
assets/qris.jpg
```

Contoh:

```text
doraemon-store/
└── assets/
    └── qris.jpg
```

Jika ingin menggunakan lokasi lain:

```env
QRIS_IMAGE=/path/ke/qris.png
```

Pastikan file benar-benar tersedia.

---

# ☆ 6. Menjalankan Bot

Jalankan:

```bash
npm start
```

Jika konfigurasi benar, bot akan melakukan koneksi ke WhatsApp.

---

# ☆ 7. Login WhatsApp

Pada pertama kali menjalankan bot, QR Code akan muncul di terminal.

Buka WhatsApp:

```text
WhatsApp
   ↓
Perangkat Tertaut
   ↓
Menautkan Perangkat
   ↓
Scan QR Code
```

Session akan disimpan secara lokal di:

```text
data/
```

Jangan menghapus data session jika tidak ingin login ulang.

---

# ☆ 8. Struktur Project

```text
doraemon-store/
│
├── assets/
│   └── qris.jpg
│
├── data/
│   └── (dibuat otomatis)
│
├── src/
│   │
│   ├── index.js
│   ├── config.js
│   │
│   ├── database/
│   │   └── database.js
│   │
│   ├── handlers/
│   │   ├── messageHandler.js
│   │   ├── menuHandler.js
│   │   ├── orderHandler.js
│   │   ├── paymentHandler.js
│   │   └── adminHandler.js
│   │
│   ├── services/
│   │   ├── orderService.js
│   │   ├── paymentService.js
│   │   ├── priceService.js
│   │   └── whatsappService.js
│   │
│   └── utils/
│       ├── formatter.js
│       ├── validator.js
│       └── logger.js
│
├── .env
├── .env.example
├── package.json
└── README.md
```

---

# ☆ Penjelasan Struktur

### `assets/`

Menyimpan file asset store.

```text
assets/qris.jpg
```

Digunakan sebagai gambar QRIS pembayaran.

---

### `data/`

Folder database dan data runtime.

Folder ini dibuat otomatis oleh aplikasi jika belum tersedia.

```text
data/
```

Jangan asal hapus folder ini karena dapat menghilangkan data database/session.

---

### `src/index.js`

Entry point utama aplikasi.

```text
index.js
   ↓
Initialize Config
   ↓
Initialize Database
   ↓
Initialize WhatsApp
   ↓
Start Message Handler
```

---

### `src/config.js`

Mengatur konfigurasi aplikasi dan membaca environment variable dari `.env`.

Contohnya:

```env
ADMIN_WA=6281234567890
QRIS_IMAGE=assets/qris.jpg
```

---

# ☆ Handlers

Folder:

```text
src/handlers/
```

Berisi logic untuk menangani pesan dan interaksi WhatsApp.

### `messageHandler.js`

Menangani pesan masuk dan menentukan command/action yang harus diproses.

### `menuHandler.js`

Menangani:

```text
.menu
.harga
.carabeli
.admin
```

### `orderHandler.js`

Menangani proses pembuatan order customer.

### `paymentHandler.js`

Menangani proses pembayaran dan bukti transfer.

### `adminHandler.js`

Menangani command khusus admin seperti:

```text
.setprice
.prices
.orders
.pending
.verify
.reject
.done
.maintenance
.broadcast
```

---

# ☆ Services

Folder:

```text
src/services/
```

Berisi logic utama aplikasi.

### `orderService.js`

Mengatur:

```text
☆ Create Order
☆ Update Order
☆ Get Order
☆ Cancel Order
☆ Order Status
```

### `paymentService.js`

Mengatur:

```text
☆ Payment Status
☆ Payment Verification
☆ Payment Rejection
☆ Payment Record
```

### `priceService.js`

Mengatur:

```text
☆ Get Price
☆ Set Price
☆ Update Price
☆ Price List
```

### `whatsappService.js`

Mengatur komunikasi dan fungsi WhatsApp bot.

---

# ☆ Utils

Folder:

```text
src/utils/
```

### `formatter.js`

Mengatur format pesan, harga, tanggal, order ID, dan output bot.

### `validator.js`

Mengvalidasi input customer dan admin.

Contohnya:

```text
☆ Username Roblox
☆ Nomor WhatsApp
☆ Order ID
☆ Harga
☆ Command
```

### `logger.js`

Digunakan untuk logging aktivitas aplikasi dan error.

---

# ☆ Database

Database menggunakan:

```text
SQLite
```

Logic database berada di:

```text
src/database/database.js
```

Database runtime disimpan di:

```text
data/
```

Database menyimpan informasi yang dibutuhkan oleh sistem seperti:

```text
☆ Customer
☆ Order
☆ Payment
☆ Price
☆ Status
```

---

# ☆ Command Customer

| Command     | Fungsi               |
| ----------- | -------------------- |
| `.menu`     | Menu utama           |
| `.harga`    | Daftar harga         |
| `.order`    | Membuat order        |
| `.status`   | Cek status order     |
| `.payment`  | Informasi pembayaran |
| `.carabeli` | Cara pembelian       |
| `.admin`    | Hubungi admin        |
| `.batal`    | Batalkan order       |

---

# ☆ Command Admin

| Command            | Fungsi                |
| ------------------ | --------------------- |
| `.prices`          | Melihat semua harga   |
| `.setprice`        | Mengubah harga        |
| `.orders`          | Melihat order         |
| `.pending`         | Melihat order pending |
| `.verify`          | Verifikasi pembayaran |
| `.reject`          | Menolak pembayaran    |
| `.done`            | Menyelesaikan order   |
| `.maintenance on`  | Aktifkan maintenance  |
| `.maintenance off` | Matikan maintenance   |
| `.broadcast`       | Broadcast customer    |

---

# ☆ Management Harga

Contoh:

```text
.setprice R148 148000
```

```text
.setprice PO_R135 135000
```

```text
.setprice VISEND_FAST_R148 148000
```

```text
.setprice VISEND_PO_R135 135000
```

Lihat seluruh harga:

```text
.prices
```

---

# ☆ Order & Payment

Customer membuat order:

```text
.order
```

Setelah order dibuat, customer mendapatkan informasi pembayaran dan QRIS.

Customer kemudian mengirim bukti pembayaran.

Bot akan meneruskan bukti tersebut kepada admin.

### Verify

```text
.verify DRB-000001
```

Hasil:

```text
Payment : PAID
Order   : PROCESSING
```

### Reject

```text
.reject DRB-000001
```

Hasil:

```text
Payment : FAILED
Order   : CANCELLED
```

### Complete

```text
.done DRB-000001
```

Hanya dapat dilakukan setelah pembayaran berstatus:

```text
PAID
```

---

# ☆ Status Order

```text
PENDING
   │
   ▼
WAITING_PAYMENT
   │
   ▼
PAYMENT_REVIEW
   │
   ├──────────────► FAILED
   │                    │
   │                    ▼
   │                CANCELLED
   │
   ▼
PAID
   │
   ▼
PROCESSING
   │
   ▼
DONE
```

---

# ☆ Maintenance Mode

Aktif:

```text
.maintenance on
```

Nonaktif:

```text
.maintenance off
```

Ketika maintenance aktif, customer akan menerima pesan maintenance.

Admin tetap dapat menjalankan command admin.

---

# ☆ Broadcast

Gunakan:

```text
.broadcast
```

Kemudian kirim pesan broadcast.

Bot akan mengirim pesan ke customer menggunakan delay antar pesan untuk membantu mengurangi risiko rate limit.

Jangan digunakan untuk spam massal. WhatsApp tidak punya kewajiban moral untuk menyukai bot kamu.

---

# ☆ Backup Database

Database berada di folder:

```text
data/
```

Jika database bernama:

```text
data/store.db
```

Backup:

```bash
mkdir -p backup
cp data/store.db backup/store-$(date +%F).db
```

Contoh:

```text
backup/
├── store-2026-09-01.db
├── store-2026-09-02.db
└── store-2026-09-03.db
```

---

# ☆ PM2 VPS

Untuk menjaga bot tetap berjalan ketika terminal ditutup:

```bash
npm install -g pm2
```

Jalankan:

```bash
pm2 start src/index.js --name doraemon-store
```

Simpan:

```bash
pm2 save
```

Cek:

```bash
pm2 status
```

Log:

```bash
pm2 logs doraemon-store
```

Restart:

```bash
pm2 restart doraemon-store
```

---

# ☆ Keamanan

Bot tidak membutuhkan informasi sensitif Roblox.

```text
✕ Password Roblox
✕ Cookie Roblox
✕ OTP Roblox
✕ PIN
✕ Token Roblox
```

Data order hanya menggunakan informasi yang diperlukan untuk proses transaksi, seperti:

```text
✓ Username Roblox
✓ Produk
✓ Informasi pembayaran
✓ Bukti pembayaran
```

Session order memiliki timeout otomatis:

```text
15 menit
```

---

# ☆ Troubleshooting

## `better-sqlite3` Error

Termux:

```bash
pkg install python clang make -y
npm install
```

Linux:

```bash
sudo apt install python3 make g++ -y
npm install
```

---

## QR Code Muncul Lagi

Periksa folder:

```text
data/
```

Pastikan session tidak terhapus.

---

## QRIS Tidak Ditemukan

Periksa:

```bash
ls -lah assets/
```

Pastikan:

```text
assets/qris.jpg
```

tersedia.

Jika menggunakan path custom, cek `.env`:

```env
QRIS_IMAGE=assets/qris.jpg
```

---

# ☆ Development

Untuk developer yang ingin memodifikasi project:

```text
Handlers
   ↓
Services
   ↓
Database
   ↓
Utils
```

Pemisahan ini membuat logic bot lebih mudah dikembangkan tanpa menumpuk seluruh kode di satu file seperti proyek sekolah yang dikerjakan 15 menit sebelum deadline.

---

# ☆ Disclaimer

DORAEMON STORE ROBLOX dibuat untuk membantu otomatisasi operasional toko Robux melalui WhatsApp.

Gunakan project sesuai:

* Ketentuan WhatsApp
* Ketentuan Roblox
* Ketentuan penyedia pembayaran
* Hukum dan peraturan yang berlaku

Developer tidak bertanggung jawab atas penyalahgunaan project, transaksi pengguna, maupun pembatasan akun akibat pelanggaran terhadap kebijakan platform.

---

<p align="center">

## ☆ DORAEMON STORE ROBLOX ☆

**WhatsApp Bot • Robux Store • Automated Order**

<br>

`☆ Simple` `☆ Fast` `☆ Automated` `☆ SQLite`

<br><br>

Made with Node.js and questionable amounts of caffeine.

</p>
