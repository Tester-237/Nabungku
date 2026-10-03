# Tabunganku (Nabungku) — proyek APK

Aplikasi web (HTML) yang dibungkus dengan Capacitor menjadi APK Android.
Folder `android/` **tidak** disertakan; dibuat otomatis saat build.

## Isi proyek

- `www/index.html` — aplikasi (Update3, awalnya kosong)
- `assets/` — folder untuk ikon kamu (kosong, lihat bagian Ikon)
- `capacitor.config.json` — nama app: Tabunganku, ID: `com.tabunganku.app`
- `codemagic.yaml` — pengaturan build di Codemagic
- `package.json`

## Langkah 1: Upload ke GitHub (lewat browser, tanpa command)

1. Ekstrak ZIP ini.
2. Buka repo kosongmu di GitHub, klik **Add file > Upload files**.
3. Tarik semua isi hasil ekstrak (`codemagic.yaml`, `package.json`, `capacitor.config.json`, folder `www` dan `assets`), lalu klik **Commit changes**.
   Pastikan `codemagic.yaml` berada di root repo, bukan di dalam subfolder.

## Langkah 2: Build di Codemagic

1. Login ke codemagic.io dengan akun GitHub.
2. **Add application**, pilih repo tadi, tipe proyek: **Other / codemagic.yaml**.
3. Klik **Start new build**, pilih workflow **Tabunganku APK (debug)**.
4. Setelah selesai (sekitar 5-10 menit), unduh APK di bagian **Artifacts**.
5. Salin APK ke HP lalu install (izinkan "Install dari sumber tidak dikenal").

APK ini bertipe **debug**, jadi bisa langsung dipasang tanpa keystore.
Untuk rilis ke Play Store, kamu perlu build release yang ditandatangani (keystore).

## Ikon aplikasi (opsional)

Taruh gambar ikonmu di folder `assets/` dengan nama:

- `icon-only.png` — 1024x1024 px, persegi penuh (wajib agar ikon dipakai)
- `icon-foreground.png` dan `icon-background.png` — 1024x1024 px (opsional, untuk ikon adaptif Android)

Kalau `icon-only.png` tidak ada, build tetap jalan dan memakai ikon bawaan Capacitor.

## Ganti nama / ID aplikasi

Edit `capacitor.config.json`:
- `appName` — nama di bawah ikon HP
- `appId` — ID unik, mis. `com.namakamu.nabungku`

## Update isi aplikasi

Ganti `www/index.html` lewat tombol Upload files di GitHub, lalu jalankan build baru di Codemagic.

## Catatan

- Data tabungan tersimpan di penyimpanan lokal aplikasi (localStorage), jadi hilang jika aplikasi di-uninstall atau datanya dihapus.
- Kunci penyimpanan: `nabungku_v2`.
