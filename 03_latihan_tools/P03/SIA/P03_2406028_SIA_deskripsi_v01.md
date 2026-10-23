# Use Case Description — Sistem Informasi Akademik (SIA)

## 1. SIA-UC01 — Ajukan KRS

**ID Use Case:** SIA-UC01  
**Aktor Utama:** Mahasiswa  
**Sumber Kebutuhan:** SIA-R03, SIA-R04, SIA-R05  
**Tujuan:** Mahasiswa berhasil mengajukan KRS dan pengajuan tersimpan dalam sistem.

### Pemicu
Mahasiswa memilih fungsi pengajuan KRS pada Sistem Informasi Akademik.

### Prasyarat
1. Mahasiswa telah terautentikasi.
2. Data mata kuliah, prasyarat, dan jadwal tersedia.

### Pascakondisi Berhasil
Pengajuan KRS tersimpan dan berstatus **Menunggu persetujuan dosen wali**.

### Pascakondisi Gagal
Pengajuan KRS belum berhasil tersimpan apabila validasi gagal.

### Relasi
- **Include:** SIA-UC02 — Validasi KRS.
- **Extend:** SIA-UC03 — Unduh bukti pengajuan KRS.
- **Extension Point:** Bukti pengajuan tersedia.
- **Kondisi Extend:** Mahasiswa memilih unduh bukti.

### Alur Utama
1. Mahasiswa membuka fungsi pengajuan KRS.
2. Sistem menampilkan formulir pengajuan KRS.
3. Mahasiswa memilih mata kuliah yang akan diajukan.
4. Mahasiswa mengirimkan pengajuan KRS.
5. Sistem memeriksa kelengkapan data dan menjalankan validasi KRS melalui SIA-UC02.
6. Jika validasi berhasil, sistem menyimpan pengajuan KRS.
7. Sistem menampilkan konfirmasi pengajuan dan status menunggu persetujuan dosen wali.
8. Mahasiswa dapat memilih mengunduh bukti pengajuan atau mengakhiri proses.

### Alur Alternatif dan Pengecualian
- **A1 — Data tidak lengkap:** Sistem memberi informasi bahwa data pengajuan belum lengkap. Pengajuan belum berhasil tersimpan.
- **A2 — Prasyarat tidak terpenuhi:** Sistem memberi informasi bahwa terdapat mata kuliah yang prasyaratnya belum terpenuhi. Pengajuan belum berhasil tersimpan.
- **A3 — Benturan jadwal:** Sistem memberi informasi bahwa terdapat jadwal mata kuliah yang bertabrakan. Pengajuan belum berhasil tersimpan.
- **A4 — Tidak mengunduh bukti:** Mahasiswa tidak memilih unduh bukti. Pengajuan tetap berhasil tersimpan apabila validasi berhasil.

---

## 2. SIA-UC02 — Validasi KRS

**ID Use Case:** SIA-UC02  
**Aktor:** Sistem Informasi Akademik  
**Use Case Pemanggil:** SIA-UC01 — Ajukan KRS  
**Sumber Kebutuhan:** SIA-R04  
**Tujuan:** Memastikan pengajuan KRS memenuhi ketentuan sebelum disimpan.

### Pemicu
Sistem menjalankan validasi setelah mahasiswa mengirimkan pengajuan KRS.

### Prasyarat
1. Mahasiswa telah mengirimkan data pengajuan KRS.
2. Data mata kuliah, prasyarat, dan jadwal tersedia.

### Pascakondisi Berhasil
Sistem menyatakan pengajuan valid dan mengembalikan hasil validasi berhasil kepada SIA-UC01.

### Pascakondisi Gagal
Sistem menyatakan pengajuan tidak valid dan mengembalikan informasi kesalahan kepada SIA-UC01. Pengajuan belum berhasil tersimpan.

### Alur Utama
1. Sistem menerima data pengajuan KRS dari SIA-UC01.
2. Sistem memeriksa kelengkapan data pengajuan.
3. Sistem memeriksa pemenuhan prasyarat mata kuliah.
4. Sistem memeriksa benturan jadwal mata kuliah.
5. Jika seluruh pemeriksaan berhasil, sistem mengembalikan hasil validasi berhasil kepada SIA-UC01.

### Alur Alternatif dan Pengecualian
- **A1 — Data tidak lengkap:** Sistem mengembalikan hasil validasi gagal beserta informasi data yang belum lengkap.
- **A2 — Prasyarat tidak terpenuhi:** Sistem mengembalikan hasil validasi gagal beserta informasi prasyarat yang belum terpenuhi.
- **A3 — Jadwal bertabrakan:** Sistem mengembalikan hasil validasi gagal beserta informasi benturan jadwal.

---

## 3. SIA-UC03 — Unduh Bukti Pengajuan KRS

**ID Use Case:** SIA-UC03  
**Aktor Utama:** Mahasiswa  
**Sumber Kebutuhan:** SIA-R05  
**Use Case Dasar:** SIA-UC01 — Ajukan KRS  
**Tujuan:** Mahasiswa memperoleh bukti pengajuan KRS yang berhasil disimpan.

### Pemicu
Mahasiswa memilih opsi unduh bukti pada tampilan konfirmasi pengajuan KRS.

### Prasyarat
1. Pengajuan KRS berhasil disimpan.
2. Sistem menampilkan konfirmasi pengajuan.
3. Mahasiswa memilih opsi unduh bukti.

### Pascakondisi Berhasil
Bukti pengajuan KRS tersedia untuk diunduh oleh mahasiswa.

### Pascakondisi Gagal
Pengajuan KRS tetap tersimpan meskipun bukti gagal disediakan atau diunduh.

### Alur Utama
1. Sistem menampilkan konfirmasi pengajuan KRS yang berhasil disimpan.
2. Mahasiswa memilih opsi unduh bukti pengajuan.
3. Sistem menyiapkan bukti berdasarkan pengajuan yang tersimpan.
4. Sistem menyediakan bukti pengajuan untuk diunduh.
5. Mahasiswa mengunduh bukti pengajuan KRS.

### Alur Alternatif dan Pengecualian
- **A1 — Mahasiswa tidak memilih unduh bukti:** Use case ini tidak dijalankan. Pengajuan KRS tetap berhasil.
- **A2 — Bukti gagal disediakan:** Sistem memberikan informasi bahwa bukti belum dapat diunduh. Pengajuan KRS tetap tersimpan.

---

## 4. SIA-UC04 — Proses Keputusan KRS

**ID Use Case:** SIA-UC04  
**Aktor Utama:** Dosen wali  
**Sumber Kebutuhan:** SIA-R06  
**Tujuan:** Dosen wali memutuskan persetujuan atau penolakan pengajuan KRS dan memberikan catatan keputusan.

### Pemicu
Dosen wali memilih pengajuan KRS yang akan diproses.

### Prasyarat
1. Dosen wali telah terautentikasi.
2. Terdapat pengajuan KRS yang tersimpan dan menunggu keputusan.

### Pascakondisi Berhasil
Keputusan dosen wali tersimpan bersama catatan keputusan. Status pengajuan diperbarui sesuai keputusan, yaitu disetujui atau ditolak.

### Pascakondisi Gagal
Keputusan belum berhasil tersimpan dan status keputusan belum diperbarui.

### Alur Utama
1. Dosen wali membuka daftar pengajuan KRS yang menunggu keputusan.
2. Sistem menampilkan daftar pengajuan KRS.
3. Dosen wali memilih salah satu pengajuan.
4. Sistem menampilkan rincian pengajuan KRS.
5. Dosen wali memilih keputusan, yaitu menyetujui atau menolak KRS.
6. Dosen wali memberikan catatan keputusan.
7. Dosen wali mengonfirmasi keputusan.
8. Sistem menyimpan keputusan dan catatan dosen wali.
9. Sistem memperbarui status pengajuan sesuai keputusan yang diberikan.
10. Sistem menampilkan konfirmasi bahwa keputusan berhasil disimpan.

### Alur Alternatif dan Pengecualian
- **A1 — Pengajuan tidak tersedia:** Sistem menampilkan informasi bahwa pengajuan yang dipilih tidak tersedia untuk diproses.
- **A2 — Keputusan atau catatan belum lengkap:** Sistem meminta dosen wali melengkapi keputusan atau catatan sebelum menyimpan.
- **A3 — Penyimpanan gagal:** Sistem menampilkan informasi kegagalan. Keputusan belum dianggap berhasil tersimpan.

---

## Aturan Bisnis dan Asumsi

1. Pengguna telah terautentikasi sebelum menggunakan fungsi sesuai perannya.
2. Data mata kuliah, prasyarat, dan jadwal tersedia untuk proses validasi.
3. Validasi yang gagal menyebabkan pengajuan KRS belum berhasil tersimpan.
4. Mengunduh bukti bukan syarat keberhasilan pengajuan KRS.
5. Pengajuan KRS yang tersimpan belum berarti telah disetujui dosen wali.
6. Proses pembayaran, pengisian nilai, dan implementasi basis data berada di luar ruang lingkup tugas ini.