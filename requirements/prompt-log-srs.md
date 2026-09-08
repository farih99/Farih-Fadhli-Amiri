Berikut adalah **prompt siap pakai** yang sudah disesuaikan dengan PRD DisiplinGuard yang Anda berikan. Cukup salin seluruh blok di bawah ini dan tempel ke GPT.

Markdown

```
[Peran]
Kamu adalah requirements analyst senior.

[Tugas]
Ubah PRD berikut menjadi DRAF SRS ringkas.

[Konteks]
PRD hasil revisi : 
DRAF PRD Ringkas: DisiplinGuard

1. Ringkasan Eksekutif
DisiplinGuard adalah produk web responsif berbasis AI yang dirancang sebagai sistem early-warning untuk membantu Guru Bimbingan Konseling (BK) dan Wali Kelas memantau serta mengidentifikasi siswa yang berisiko mengalami penurunan kedisiplinan.
Produk ini memanfaatkan data absensi dan prestasi akademik yang selama ini terutama digunakan untuk kebutuhan administratif. Dengan memanfaatkan pola dari data tersebut, DisiplinGuard memberikan prediksi tingkat kedisiplinan siswa menjadi tinggi, sedang, atau rendah, disertai skor risiko dan rekomendasi intervensi.
Prioritas produk bukan menggantikan keputusan guru, melainkan mempercepat proses identifikasi siswa yang membutuhkan perhatian. Hal ini relevan karena penelitian pada 711 siswa kelas X–XII dari 4 jurusan menunjukkan adanya hubungan antara kehadiran, alfa, keterlambatan, prestasi akademik, dan tingkat kedisiplinan. Model klasifikasi yang diuji juga mampu mencapai akurasi hingga 77,62% menggunakan Naive Bayes.

2. Problem Statement & Bukti
Problem Statement
Guru BK dan Wali Kelas menghadapi jumlah siswa yang besar sehingga pemantauan kedisiplinan secara manual berdasarkan data absensi dan nilai menjadi kurang efektif. Data yang tersedia belum dimanfaatkan secara optimal untuk memberikan peringatan dini. Akibatnya, intervensi terhadap siswa yang mulai menunjukkan pola ketidakdisiplinan berpotensi dilakukan setelah masalah berkembang.

Fakta
| Fakta                                                                                            | Bukti dari konteks                                                    |
| ------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- |
| Data absensi dan prestasi akademik selama ini terutama digunakan untuk administrasi              | Data digunakan untuk rekap kehadiran dan pelaporan nilai              |
| Terdapat pola hubungan antara faktor absensi, keterlambatan, prestasi akademik, dan kedisiplinan | Dataset aktual 711 siswa menunjukkan hubungan yang signifikan         |
| Dataset mencakup siswa kelas X–XII                                                               | Data berasal dari tiga tingkat kelas                                  |
| Dataset berasal dari 4 jurusan                                                                   | Cakupan data mencakup empat jurusan                                   |
| Model klasifikasi dapat memprediksi kategori kedisiplinan                                        | Decision Tree, KNN, dan Naive Bayes diuji                             |
| Performa terbaik mencapai akurasi 77,62%                                                         | Naive Bayes memperoleh akurasi hingga 77,62%                          |
| Fitur penting telah teridentifikasi                                                              | Persentase absensi, jumlah alfa, keterlambatan, dan prestasi akademik |
| Sekolah membutuhkan pengambilan keputusan berbasis data                                          | Sekolah menyatakan kebutuhan sistem untuk intervensi preventif        |

Asumsi
| Kode        | Asumsi                                                                                                                            |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [ASUMSI-01] | Guru BK dan Wali Kelas memiliki akses terhadap data absensi serta prestasi akademik siswa yang diperlukan untuk penggunaan produk |
| [ASUMSI-02] | Kategori kedisiplinan tinggi, sedang, dan rendah dapat digunakan sebagai kategori operasional dalam produk                        |
| [ASUMSI-03] | Rekomendasi intervensi yang diberikan sistem digunakan sebagai bahan pertimbangan, bukan keputusan otomatis terhadap siswa        |
| [ASUMSI-04] | Prototype dapat diuji menggunakan sebagian atau seluruh data historis yang tersedia selama periode pengembangan                   |
| [ASUMSI-05] | Pengguna mampu mengoperasikan browser melalui komputer sekolah maupun smartphone                                                  |

3. Target User & Stakeholder
| Peran                                 | Kebutuhan                                                                                | Pengaruh |
| ------------------------------------- | ---------------------------------------------------------------------------------------- | -------- |
| Guru BK                               | Mengetahui siswa berisiko, melihat tingkat risiko, dan memperoleh rekomendasi intervensi | Tinggi   |
| Wali Kelas                            | Memantau kondisi kedisiplinan siswa dalam kelas secara cepat                             | Tinggi   |
| Kepala Sekolah                        | Mendapatkan gambaran umum kondisi kedisiplinan siswa                                     | Tinggi   |
| Wakil Kepala Sekolah Bidang Kesiswaan | Memantau pola kedisiplinan sebagai dasar evaluasi dan pembinaan                          | Tinggi   |
| Manajemen Sekolah                     | Mendapatkan informasi pendukung dalam pengambilan keputusan sekolah                      | Sedang   |
| Guru Mata Pelajaran                   | Mendukung pemantauan kondisi siswa melalui informasi yang relevan                        | Sedang   |

Prioritas Pengguna
Primary user: Guru BK dan Wali Kelas.
Secondary user: Kepala Sekolah, Wakil Kepala Sekolah Bidang Kesiswaan, Manajemen Sekolah, dan Guru Mata Pelajaran.

4. Value Proposition
Pain yang Dikurangi
DisiplinGuard mengurangi beberapa beban utama pengguna:
1. Pemantauan manual berskala besar
2. Keterlambatan identifikasi masalah
3. Kesulitan membaca data mentah
4. Sulit menentukan prioritas intervensi

Gain yang Diciptakan
- Visibilitas risiko
- Prioritas tindakan
- Keputusan berbasis data
- Efisiensi pemantauan
- Intervensi preventif

Mengapa AI Bukan Gimmick
Fitur AI memiliki fungsi substantif karena problem yang dihadapi adalah identifikasi pola risiko dari sejumlah besar data siswa. Empat variabel utama (persentase absensi, jumlah alfa, keterlambatan, dan prestasi akademik) telah teridentifikasi berpengaruh. Pengujian dataset 711 siswa menunjukkan akurasi hingga 77,62%.

5. Tujuan Produk & KPI Terukur
| Tujuan                                        | KPI                                                                          | Cara Mengukur                                                        |
| --------------------------------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Membantu mendeteksi siswa yang berisiko       | Akurasi prediksi ≥ 77% pada evaluasi prototype                               | Mengukur akurasi model pada data pengujian                           |
| Menghasilkan klasifikasi risiko yang relevan  | F1-score memadai pada kategori kedisiplinan                                  | Mengukur precision, recall, dan F1-score pada data pengujian         |
| Mempermudah guru menentukan prioritas         | ≥ 80% pengguna uji dapat menemukan siswa berisiko melalui sistem             | Pengujian tugas kepada pengguna prototype                            |
| Mengurangi kebutuhan analisis data mentah     | ≥ 70% pengguna uji menyatakan pemantauan lebih mudah                         | Kuesioner setelah penggunaan prototype                               |
| Mendukung intervensi preventif                | ≥ 70% siswa berisiko yang teridentifikasi memiliki rekomendasi tindak lanjut | Membandingkan daftar siswa berisiko dengan rekomendasi yang tersedia |
| Produk dapat digunakan pada perangkat berbeda | Seluruh fitur utama dapat digunakan melalui browser desktop dan smartphone   | Pengujian fungsional pada kedua jenis perangkat                      |

6. Scope Fitur 3 Bulan: MoSCoW
| Prioritas   | Fitur                                            | Deskripsi                                                                    |
| ----------- | ------------------------------------------------ | ---------------------------------------------------------------------------- |
| Must Have   | Dashboard monitoring                             | Menampilkan kondisi kedisiplinan siswa secara ringkas                        |
| Must Have   | Data siswa                                       | Menampilkan informasi siswa dan indikator yang berkaitan dengan kedisiplinan |
| Must Have   | Pemantauan absensi                               | Menampilkan persentase kehadiran, alfa, dan keterlambatan                    |
| Must Have   | Pemantauan prestasi akademik                     | Menampilkan indikator prestasi akademik siswa                                |
| Must Have   | ★ Prediksi tingkat kedisiplinan                  | Mengklasifikasikan siswa menjadi tinggi, sedang, atau rendah                 |
| Must Have   | ★ Skor risiko                                    | Memberikan representasi tingkat risiko siswa berdasarkan hasil prediksi      |
| Must Have   | ★ Rekomendasi intervensi                         | Memberikan saran tindak lanjut berdasarkan kategori risiko                   |
| Must Have   | Daftar prioritas siswa berisiko                  | Membantu guru memusatkan perhatian pada siswa yang perlu ditindaklanjuti     |
| Should Have | Detail siswa                                     | Menampilkan ringkasan faktor yang berhubungan dengan hasil prediksi          |
| Should Have | Filter siswa                                     | Penyaringan berdasarkan kelas, jurusan, atau kategori risiko                 |
| Should Have | Riwayat pemantauan                               | Menyimpan catatan pemantauan/intervensi yang dilakukan                       |
| Should Have | Tampilan mobile-responsive                       | Memastikan fungsi utama tetap nyaman digunakan melalui smartphone            |
| Could Have  | Ringkasan kondisi kelas                          | Menampilkan gambaran tingkat kedisiplinan satu kelas                         |
| Could Have  | Ringkasan untuk pimpinan sekolah                 | Menampilkan informasi agregat untuk kebutuhan pemantauan                     |
| Could Have  | Notifikasi risiko                                | Pemberitahuan ketika terdapat siswa dengan risiko tertentu                   |
| Won't Have  | Otomatisasi keputusan disipliner                 | Sistem tidak menentukan hukuman atau tindakan disiplin secara otomatis       |
| Won't Have  | Integrasi kompleks dengan seluruh sistem sekolah | Integrasi luas dengan sistem existing berada di luar scope prototype         |
| Won't Have  | Model AI kompleks                                | Prototype tidak berfokus pada model dengan kebutuhan komputasi tinggi        |

7. Non-Goals Eksplisit
DisiplinGuard tidak ditujukan untuk:
1. Menggantikan peran Guru BK, Wali Kelas, atau pihak sekolah dalam mengambil keputusan.
2. Menentukan hukuman atau sanksi siswa secara otomatis.
3. Menjadi sistem administrasi akademik atau absensi utama sekolah.
4. Melakukan prediksi di luar kategori kedisiplinan yang telah ditentukan.
5. Mengklaim bahwa prediksi AI merupakan diagnosis pasti terhadap perilaku siswa.
6. Menjadi sistem AI berskala besar dengan kebutuhan komputasi tinggi.
7. Melakukan integrasi penuh dengan seluruh sistem informasi sekolah.
8. Menggeneralisasikan hasil model secara langsung kepada seluruh sekolah karena data penelitian masih terbatas pada satu sekolah.

8. Asumsi & Risiko Utama + Mitigasi
(seperti tercantum di PRD)

Fokus Produk 3 Bulan
MVP berpusat pada alur: Data siswa → indikator absensi & prestasi → ★ prediksi tingkat kedisiplinan → ★ skor risiko → ★ rekomendasi intervensi → guru menentukan tindak lanjut.

Acuan kualitas    : ISO/IEC 25010 (karakteristik relevan: Functional Suitability, Performance Efficiency, Usability, Reliability, Security, Maintainability)
Prioritas         : MoSCoW
Platform & stack  : Web (prioritas) + Mobile-responsive — dapat diakses melalui browser di komputer sekolah maupun smartphone guru.

[Format output]
1) Tujuan, scope, definisi istilah;
2) User & stakeholder, lingkungan operasi, asumsi & dependensi;
3) FR: tabel FR-01..FR-n — pola "Sistem harus dapat <aksi> <objek> saat <kondisi> → <output>" + ID, prioritas MoSCoW, metode verifikasi;
4) NFR: tabel NFR-01..NFR-m — kategori ISO/IEC 25010 + metrik + target + kondisi ukur (wajib: akurasi & latensi AI, keamanan, privasi, usability);
5) Kebutuhan data minimum fitur AI (input → output model);
6) Aturan bisnis hasil riset;
7) Matriks traceability: FR/NFR → fitur PRD terkait.

[Aturan]
- Setiap FR/NFR harus dapat ditelusuri ke bukti pada PRD/riset; dilarang menambah kebutuhan tanpa bukti.
- Bila pembahasan mulai masuk arsitektur/UI, hentikan (itu urusan HLD/LLD).
- Bahasa Indonesia baku, format Markdown.
```