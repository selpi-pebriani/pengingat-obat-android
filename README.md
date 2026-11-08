# 💊 Pengingat Obat

Aplikasi Android sederhana untuk membantu mengingat jadwal minum **obat** dan **vitamin** setiap hari. Pengaturan pengguna disimpan di perangkat memakai **SharedPreferences**, sedangkan daftar jadwal disimpan sementara di memori.

> Studi kasus SharedPreferences (Tugas Pemrograman Mobile, UMKO) - Selpi Pebriani, 2459201053, 5A.

---

## ✨ Fitur

- 📋 **Daftar jadwal** obat dan vitamin lengkap dengan jam minum
- 💊🍊 **Ikon pembeda**: kapsul untuk obat, jeruk untuk vitamin
- ✅ **Penanda status**: tampil *Sudah diminum* (hijau, nama dicoret) atau *Belum diminum* (pink)
- 📊 **Progres harian**, misalnya 1 / 2 jadwal sudah diminum
- ✎ **Ubah nama pengguna**, sapaan tampil sebagai "Halo, (nama)"
- 💾 **Pengaturan tersimpan** (nama pengguna dan jenis Obat/Vitamin) dengan SharedPreferences
- ⚠️ Daftar jadwal disimpan sementara di memori, jadi hilang saat aplikasi ditutup
- ℹ️ Tombol **Tentang aplikasi** berisi ringkasan penjelasan aplikasi

---

## 🧩 Struktur Kode

| File | Fungsi |
|------|--------|
| `MainActivity` | Layar utama: daftar jadwal, progres, dan pembacaan pengaturan di `onResume()` |
| `Pengingat` | Model data (nama, jenis obat/vitamin, jam, status minum) |
| `PengingatAdapter` | Adapter untuk menampilkan setiap item jadwal di ListView |
| `PrefsManager` | Membungkus SharedPreferences untuk menyimpan dan membaca pengaturan |

---

## 💾 Pembagian Data

**Disimpan di SharedPreferences (`PrefsManager`):**

| Data | Tipe | Alasan |
|------|------|--------|
| Nama pengguna | String | Pengaturan kecil berbentuk key-value, satu nilai per kunci |
| Jenis terakhir dipilih (Obat/Vitamin) | Boolean | Tidak perlu dicari atau difilter, cukup ringan dan sederhana |

**Tidak disimpan permanen (`ArrayList<Pengingat>` di `MainActivity`):**

| Data | Alasan |
|------|--------|
| Daftar jadwal dan status sudah/belum diminum | Jumlahnya terus bertambah dan butuh operasi hapus, ubah status, serta pengurutan, sehingga lebih cocok memakai database (Room/SQLite) |

---

## ⚙️ Cara Kerja Penyimpanan

- `PrefsManager` membuat SharedPreferences bernama `pengingat_prefs` dengan mode `MODE_PRIVATE`.
- Data disimpan dengan `apply()`, yang bekerja di latar belakang sehingga tampilan tidak tersendat.
- Data dibaca kembali di `onResume()`, lalu ditampilkan ke layar.

---

## 🛠️ Teknologi

- **Bahasa:** Java
- **IDE:** Android Studio
- **Penyimpanan lokal:** SharedPreferences
- **Komponen UI:** ListView, ArrayAdapter, Custom Layout XML

---

## 🚀 Cara Menjalankan

1. Clone repositori ini:
   ```bash
   git clone https://github.com/selpi-pebriani/pengingat-obat-android.git
   ```
2. Buka folder proyek dengan **Android Studio**.
3. Tunggu proses **Gradle Sync** selesai.
4. Hubungkan perangkat Android atau jalankan emulator.
5. Klik tombol **Run ▶️**.

---

## 👩‍💻 Pembuat

| | |
|---|---|
| **Nama** | Selpi Pebriani |
| **NIM** | 2459201053 |
| **Kelas** | 5A |
| **Mata Kuliah** | Pemrograman Mobile |
| **Kampus** | Universitas Muhammadiyah Kotabumi |

---

⭐ Kalau proyek ini bermanfaat, jangan lupa beri bintang!
