# DORAEMON STORE ROBLOX - Bot WhatsApp Top Up Robux

Bot WhatsApp untuk melayani pembelian Robux.
Berjalan di Termux Android, Linux, dan VPS.

## 1. Instalasi Node.js

**Linux / VPS:**
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs git
```

**Termux (Android):**
```bash
pkg update -y
pkg install nodejs-lts git python clang make -y
```

Versi minimal: **Node.js 20**

## 2. Instalasi Project

```bash
git clone <url-repo-anda> doraemon-store
cd doraemon-store
npm install
```

Catatan Termux: `better-sqlite3` dikompilasi saat install.
Paket `python clang make` di atas sudah mencakup kebutuhannya.

## 3. Konfigurasi .env

```bash
cp .env.example .env
nano .env
```

## 4. Memasukkan Nomor Admin

Edit `ADMIN_WA` di file `.env` (format internasional, tanpa +):

```env
ADMIN_WA=6281234567890
```

## 5. Memasukkan Gambar QRIS

Simpan gambar QRIS Anda sebagai:

```
assets/qris.jpg
```

Atau ubah lokasi di `.env`:

```env
QRIS_IMAGE=/path/ke/qris.png
```

## 6. Menjalankan Bot

```bash
npm start
```

Agar tetap jalan setelah terminal tertutup (VPS):

```bash
npm install -g pm2
pm2 start src/index.js --name doraemon-store
pm2 save
```

## 7. Login WhatsApp

Saat pertama dijalankan, QR Code muncul di terminal.
Scan dengan WhatsApp: **Perangkat Tertaut > Menautkan Perangkat**.

Session tersimpan di `data/session`. Restart bot TIDAK perlu
scan ulang selama folder session tidak dihapus.

## 8. Mengubah Harga

Dari nomor admin, kirim:

```
.setprice R148 148000
.setprice PO_R135 135000
.setprice VISEND_FAST_R148 148000
.setprice VISEND_PO_R135 135000
```

Lihat semua harga dengan `.prices`.

## 9. Melihat Order

```
.orders   -> 30 order terakhir
.pending  -> order yang menunggu pembayaran/verifikasi
```

## 10. Verifikasi Pembayaran

Customer mengirim bukti transfer (gambar) -> bot meneruskan ke admin.

```
.verify DRB-000001   -> Payment: PAID, Order: PROCESSING
.reject DRB-000001   -> Payment: FAILED, Order: CANCELLED
```

## 11. Menyelesaikan Order

```
.done DRB-000001
```

Hanya berhasil jika Payment Status sudah `PAID`.

## 12. Maintenance

```
.maintenance on    -> customer menerima pesan maintenance
.maintenance off   -> store normal kembali
```

Admin tetap bisa memakai semua command admin saat maintenance.

## 13. Broadcast

```
.broadcast
```

Lalu kirim isi pesan broadcast di chat berikutnya.
Pesan dikirim ke semua customer dengan delay antar pesan
(rate limit) untuk mengurangi risiko pembatasan akun.

## 14. Backup Database

Database SQLite berada di:

```
data/store.db
```

Backup manual:

```bash
cp data/store.db backup/store-$(date +%F).db
```

Atau otomatis via cron (VPS), harian pukul 02.00:

```
0 2 * * * cp /root/doraemon-store/data/store.db /root/backup/store-$(date +\%F).db
```

## Command Customer

| Command | Fungsi |
|---|---|
| .menu | Menu utama |
| .harga | Daftar harga |
| .order | Buat pesanan |
| .status | Cek status order |
| .payment | Info pembayaran |
| .carabeli | Cara pembelian |
| .admin | Hubungi admin |
| .batal | Batalkan proses order |

## Keamanan

- Bot TIDAK pernah meminta password, cookie, OTP, PIN, atau token Roblox.
- Hanya username Roblox publik yang dibutuhkan untuk order.
- Session order timeout otomatis 15 menit.
