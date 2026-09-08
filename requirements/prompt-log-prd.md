[Peran]
Kamu adalah product manager senior untuk produk Mobile/Web berfitur AI.

[Tugas]
Susun DRAF PRD ringkas untuk "DisiplinGuard" berdasarkan kasus berikut.

[Konteks]
Problem statement : Data absensi harian dan prestasi akademik siswa di SMK Swasta RK Bintang Timur Pematangsiantar selama ini hanya digunakan untuk keperluan administratif (rekap kehadiran & pelaporan nilai). Data tersebut belum dimanfaatkan secara optimal sebagai dasar pengambilan keputusan untuk deteksi dini siswa yang berisiko mengalami penurunan kedisiplinan. Akibatnya, intervensi terhadap siswa bermasalah sering dilakukan terlambat, sehingga berdampak pada iklim belajar, prestasi individu, dan kualitas lulusan.

Target user        : Guru Bimbingan Konseling (BK) dan Wali Kelas di SMK Swasta RK Bintang Timur Pematangsiantar (dan SMK sejenis).

Stakeholder lain    : Kepala Sekolah, Wakil Kepala Sekolah Bidang Kesiswaan, Manajemen Sekolah, Guru Mata Pelajaran.

Persona ringkas     : Guru BK/Wali Kelas yang memiliki banyak siswa (ratusan), terbatas waktu, ingin memantau kedisiplinan secara proaktif, dan membutuhkan sistem early-warning yang mudah digunakan tanpa harus menganalisis data mentah secara manual.

Bukti riset         : 
- Dataset aktual 711 siswa (kelas X–XII, 4 jurusan) menunjukkan adanya pola hubungan signifikan antara persentase kehadiran, jumlah ketidakhadiran tanpa keterangan (alfa), keterlambatan, dan rata-rata nilai akademik dengan tingkat kedisiplinan.
- Model klasifikasi (Decision Tree, KNN, Naive Bayes) mampu memprediksi kategori kedisiplinan dengan akurasi hingga 77,62% (Naive Bayes) dan F1-score yang memadai.
- Fitur paling berpengaruh: persentase absensi, jumlah alfa, keterlambatan, dan prestasi akademik.
- Sekolah menyatakan kebutuhan sistem pendukung keputusan berbasis data untuk intervensi preventif.

Platform & stack    : Web (prioritas) + Mobile-responsive — dapat diakses melalui browser di komputer sekolah maupun smartphone guru.

Fitur AI inti       : Prediksi tingkat kedisiplinan siswa (tinggi / sedang / rendah) berdasarkan pola absensi dan prestasi akademik, dilengkapi skor risiko dan rekomendasi intervensi.

Konstrain           : Prototype harus selesai dalam 1 semester; data historis terbatas (hanya dari satu sekolah); biaya komputasi AI harus rendah (model ringan); integrasi dengan sistem absensi/nilai existing seminimal mungkin.

[Format output]
1) Ringkasan eksekutif;
2) Problem statement & bukti (pisahkan fakta vs asumsi);
3) Target user & stakeholder (tabel peran–kebutuhan–pengaruh);
4) Value proposition: pain yang dikurangi, gain yang diciptakan, mengapa fitur AI bukan gimmick;
5) Tujuan produk & KPI terukur (+ cara mengukurnya);
6) Scope fitur 3 bulan: tabel MoSCoW (fitur AI bertanda ★);
7) Non-goals eksplisit;
8) Asumsi & risiko utama + mitigasi.

[Aturan]
- Hanya gunakan data pada [Konteks]; bila kurang, tulis [ASUMSI-XX] lalu lanjutkan.
- Jangan menulis solusi teknis/arsitektur (itu urusan SRS/HLD/LLD).
- Bahasa Indonesia baku, format Markdown.