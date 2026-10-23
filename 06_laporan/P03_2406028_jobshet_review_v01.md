## Langkah 8 — Review dan Revisi

### A. Hasil Review

Review dilakukan untuk memeriksa kesesuaian diagram use case dan use case description Sistem Informasi Akademik (SIA), khususnya pada proses pengajuan Kartu Rencana Studi (KRS).

| No. | Aspek yang Ditinjau | Hasil Pemeriksaan | Perbaikan |
|---|---|---|---|
| 1 | Arah panah `«include»` | Panah mengarah dari Ajukan KRS ke Validasi KRS. | Dipertahankan karena sudah sesuai. |
| 2 | Arah panah `«extend»` | Panah mengarah dari Unduh bukti pengajuan KRS ke Ajukan KRS. | Dipertahankan karena sudah sesuai. |
| 3 | Kondisi extend | Pengunduhan dilakukan jika mahasiswa memilih unduh bukti. | Kondisi dicantumkan pada diagram dan deskripsi SIA-UC03. |
| 4 | Extension point | Bukti pengajuan tersedia. | Dicantumkan pada use case dasar Ajukan KRS. |
| 5 | Pascakondisi berhasil | Pengajuan tersimpan dengan status Menunggu persetujuan dosen wali. | Dipastikan konsisten dalam deskripsi SIA-UC01. |
| 6 | Pascakondisi gagal | Pengajuan tidak berhasil tersimpan apabila validasi gagal. | Dicantumkan dalam deskripsi SIA-UC01 dan SIA-UC02. |
| 7 | Nama dan ID use case | Nama use case harus sama antara katalog, diagram, dan deskripsi. | Menggunakan SIA-UC01 sampai SIA-UC04 secara konsisten. |

### B. Hasil Revisi

Berdasarkan pemeriksaan rancangan, perbaikan yang perlu dipastikan adalah sebagai berikut:

1. Memastikan diagram menggunakan empat use case, yaitu Ajukan KRS, Validasi KRS, Unduh bukti pengajuan KRS, dan Proses keputusan KRS.
2. Memastikan relasi `«include»` menghubungkan Ajukan KRS dengan Validasi KRS.
3. Memastikan relasi `«extend»` menghubungkan Unduh bukti pengajuan KRS dengan Ajukan KRS.
4. Menambahkan kondisi `[mahasiswa memilih unduh bukti]` dan extension point `Bukti pengajuan tersedia`.
5. Memastikan pengajuan tetap berhasil tersimpan apabila mahasiswa tidak mengunduh bukti.
6. Memastikan validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
7. Memastikan proses keputusan KRS mencakup persetujuan atau penolakan oleh dosen wali beserta catatan keputusan.

### Kesimpulan

Berdasarkan checklist, rancangan Sistem Informasi Akademik perlu memastikan keterkaitan antara kebutuhan, diagram use case, dan use case description. Relasi `«include»` digunakan untuk validasi KRS yang wajib dilakukan, sedangkan `«extend»` digunakan untuk pengunduhan bukti yang bersifat opsional.

Tugas dinyatakan lengkap setelah diagram dan deskripsi diperiksa, berkas sumber serta ekspor tersimpan dengan benar, dan hasil review aktual didokumentasikan.