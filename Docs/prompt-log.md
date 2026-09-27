```markdown
[Peran]
Kamu adalah software architect senior untuk aplikasi Mobile/Web berfitur AI.

[Tugas]
Buat DRAF HLD dari PRD, SRS, dan user story berikut.

[Konteks]
PRD hasil revisi :
DRAF PRD Ringkas: DisiplinGuard
1. Ringkasan Eksekutif
DisiplinGuard adalah produk web responsif berbasis AI yang dirancang sebagai sistem early-warning untuk membantu Guru Bimbingan Konseling (BK) dan Wali Kelas memantau serta mengidentifikasi siswa yang berisiko mengalami penurunan kedisiplinan.
Produk ini memanfaatkan data absensi dan prestasi akademik yang selama ini terutama digunakan untuk kebutuhan administratif. Dengan memanfaatkan pola dari data tersebut, DisiplinGuard memberikan prediksi tingkat kedisiplinan siswa menjadi tinggi, sedang, atau rendah, disertai skor risiko dan rekomendasi intervensi.
Prioritas produk bukan menggantikan keputusan guru, melainkan mempercepat proses identifikasi siswa yang membutuhkan perhatian. Hal ini relevan karena penelitian pada 711 siswa kelas X–XII dari 4 jurusan menunjukkan adanya hubungan antara kehadiran, alfa, keterlambatan, prestasi akademik, dan tingkat kedisiplinan. Model klasifikasi yang diuji juga mampu mencapai akurasi hingga 77,62% menggunakan Naive Bayes.
2. Problem Statement & Bukti (lengkap seperti di dokumen)
3. Target User & Stakeholder (Guru BK dan Wali Kelas sebagai primary user)
4. Value Proposition (pain reduction + AI bukan gimmick)
5. Tujuan Produk & KPI Terukur (akurasi ≥ 77%, F1-score memadai, ≥ 80% pengguna menemukan siswa berisiko, dll.)
6. Scope Fitur 3 Bulan: MoSCoW (Must Have: Dashboard, Data siswa, Absensi, Prestasi, ★ Prediksi, ★ Skor risiko, ★ Rekomendasi, Daftar prioritas; Should Have: Detail, Filter, Riwayat, Mobile-responsive)
7. Non-Goals (tidak menggantikan keputusan guru, tidak otomatisasi sanksi, tidak model AI kompleks, dll.)
8. Asumsi & Risiko + Mitigasi

SRS hasil revisi — FR fitur AI + NFR performa/akurasi/privasi :
FR-07 ★ Sistem harus dapat memprediksi tingkat kedisiplinan saat data indikator siswa tersedia → sistem menghasilkan kategori tinggi, sedang, atau rendah (Must Have)
FR-08 ★ Sistem harus dapat menghasilkan skor risiko saat hasil prediksi kedisiplinan tersedia → sistem menampilkan representasi tingkat risiko siswa (Must Have)
FR-09 ★ Sistem harus dapat memberikan rekomendasi intervensi saat hasil prediksi tersedia → sistem menampilkan saran tindak lanjut berdasarkan kategori risiko (Must Have)
FR-01, FR-02, FR-03, FR-04, FR-05, FR-06, FR-10 (Must Have pendukung)
FR-11, FR-12, FR-13, FR-14 (Should Have)

NFR-01: Akurasi prediksi AI ≥ 77%
NFR-02: F1-score memadai
NFR-03: Latensi prediksi AI [ASUMSI-07] ≤ 3 detik
NFR-04: Seluruh fitur utama dapat digunakan pada browser desktop dan smartphone
NFR-08: Perlindungan akses terhadap data siswa
NFR-09: Privasi data siswa (data hanya digunakan sesuai fungsi sistem)
NFR-11: ≥ 70% siswa berisiko memiliki rekomendasi tindak lanjut

Kebutuhan data minimum AI: Persentase kehadiran, Jumlah alfa, Jumlah keterlambatan, Prestasi akademik/rata-rata nilai
Output AI: Kategori (tinggi/sedang/rendah) + Skor risiko + Rekomendasi intervensi
Model yang pernah diuji: Decision Tree, KNN, Naive Bayes (akurasi terbaik 77,62%)

User stories/AC P3 :
US-06 ★ Prediksi tingkat kedisiplinan (FR-07)
US-07 ★ Melihat skor risiko (FR-08)
US-08 ★ Mendapatkan rekomendasi intervensi (FR-09)
US-01 s.d. US-05, US-10, US-14 (Must Have pendukung)
US-09, US-11, US-12, US-13 (Should Have)
Acceptance Criteria mencakup happy path (hasil ≤ 3 detik), edge case data batas, fallback data tidak lengkap, dan evaluasi akurasi ≥ 77%.

Platform & stack : Web (prioritas) + Mobile-responsive — dapat diakses melalui browser di komputer sekolah maupun smartphone guru.

Konstrain : prototype 1 semester; satu fitur AI inti (klasifikasi kedisiplinan); biaya minimal; model ringan (tidak kompleks); integrasi sistem existing seminimal mungkin.

[Format output]
1) Diagram arsitektur (Mermaid/ASCII): client → backend API → AI service → data store → layanan eksternal (bila ada);
2) Deskripsi komponen: peran, tanggung jawab, teknologi usulan. Untuk keputusan penting (mis. AI on-device vs cloud API vs library lokal) sajikan tabel trade-off: akurasi, latensi, biaya, privasi, effort, lalu beri rekomendasi;
3) Aliran data end-to-end fitur AI: input → preprocessing → inference → postprocessing → output → penyimpanan, termasuk titik fallback saat model gagal/tidak tersedia;
4) Kontrak antarkomponen tingkat tinggi: API utama, format data, pemicu/event;
5) Penempatan security & privacy by design: auth, enkripsi, data sensitif, logging;
6) Lingkungan deployment ringkas (development/staging/production).

[Aturan]
- Desain hanya dari FR/NFR yang ada; jangan menambah fitur. Gap apa pun → [ASUMSI-XX].
- Jangan masuk detail class/method/query (itu LLD).
- Setiap keputusan besar diberi alasan 1–2 kalimat + alternatif.
- Bahasa Indonesia baku.
```



```markdown
[Peran]
Kamu adalah software engineer senior (sesuai stack tim).

[Tugas]
Buat DRAF LLD untuk fitur prioritas Must pada SRS berdasarkan HLD hasil revisi.

[Konteks]
SRS hasil revisi — FR/NFR yang akan diimplementasikan :
FR Must Have:
- FR-01: Dashboard ringkasan kondisi kedisiplinan
- FR-02: Menampilkan data siswa + indikator kedisiplinan
- FR-03: Menampilkan persentase kehadiran
- FR-04: Menampilkan jumlah alfa
- FR-05: Menampilkan keterlambatan
- FR-06: Menampilkan prestasi akademik
- FR-07 ★: Prediksi tingkat kedisiplinan (tinggi/sedang/rendah)
- FR-08 ★: Menghasilkan skor risiko
- FR-09 ★: Memberikan rekomendasi intervensi
- FR-10: Daftar prioritas siswa berisiko

NFR terkait:
- NFR-01: Akurasi prediksi AI ≥ 77%
- NFR-02: F1-score memadai
- NFR-03: Latensi prediksi AI ≤ 3 detik [ASUMSI-07]
- NFR-04: Fitur utama berjalan di desktop & smartphone
- NFR-08 & NFR-09: Security & privasi data siswa
- NFR-11: ≥ 70% siswa berisiko memiliki rekomendasi

Input minimum AI: persentase kehadiran, jumlah alfa, jumlah keterlambatan, prestasi akademik/rata-rata nilai
Output AI: kategori kedisiplinan + skor risiko + rekomendasi intervensi
Model baseline yang pernah diuji: Decision Tree, KNN, Naive Bayes (akurasi terbaik 77,62% Naive Bayes)

HLD hasil revisi — komponen & kontrak API :
Arsitektur:
Client (Web Browser Desktop/Smartphone) → Backend API (Laravel 12) → AI Service (Python + scikit-learn) → Data Store (MySQL)

Komponen:
- Client Web: menampilkan dashboard, data siswa, hasil AI, rekomendasi
- Backend API: validasi, business logic, orkestrasi AI, access control
- AI Service: preprocessing, inference model klasifikasi, menghasilkan kategori + skor risiko
- Data Store: data siswa, absensi, nilai, hasil prediksi

Keputusan AI: AI Service lokal (bukan cloud/on-device) karena biaya rendah & privasi data siswa.
Model baseline: Naive Bayes [ASUMSI-06]

Kontrak API tingkat tinggi:
- API-01 Request Prediksi: input {student_id, attendance_percentage, alpha_count, late_count, average_score} → output {discipline_category, risk_score, recommendation}
- API-02 Daftar Prioritas Siswa Berisiko
- API-03 Detail Siswa (indikator)

Aliran AI: Validasi input → Preprocessing → Inference → Postprocessing (kategori + skor + rekomendasi) → Simpan hasil → Fallback jika data tidak lengkap atau AI gagal/timeout

Stack & pola :
- Client: HTML/CSS/JavaScript atau framework web ringan (responsive)
- Backend: Laravel 12
- AI Service: Python + scikit-learn
- Database: MySQL
- Pola: Clean Architecture / Layered Architecture (pemisahan Backend API dan AI Service)

[Format output]
1) Desain modul/class 2–3 fitur Must terpenting (termasuk fitur AI): tanggung jawab, atribut kunci, method utama — cukup detail agar siap dikode;
2) Skema data: entitas, relasi, constraint (SQL/Prisma/ERD teks);
3) Spesifikasi API detail endpoint inti: method, path, request/response (contoh JSON), daftar kode error;
4) Sequence/alur detail fitur AI: validasi input → preprocessing → pemanggilan model/API → fallback → respons; sertakan skenario timeout & kegagalan model;
5) Rancangan error handling & fallback (retry, pesan ramah, mode offline);
6) Tabel traceability: elemen desain ↔ ID FR/NFR.

[Aturan]
- Turunkan dari SRS/HLD; DILARANG mengubah requirement.
- Pilihan yang belum diputuskan (library, dsb.): sarankan 2 opsi + kriteria pilih, lalu tulis [KEPUTUSAN TIM: ...] yang wajib diisi tim.
- Nama class/field bahasa Inggris; penjelasan Bahasa Indonesia.
- Bahasa Indonesia baku.
```