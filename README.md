# Praktikum5_SQL_JOIN

## **SQL JOIN**

SQL JOIN adalah operasi yang digunakan untuk menggabungkan baris dari dua atau lebih tabel berdasarkan kondisi yang ditentukan. Dengan menggunakan JOIN, Anda dapat mengambil data yang terkait dari tabel yang berbeda dalam satu query.
ada beberapa jenis JOIN dalam SQL, termasuk:

1. INNER JOIN: Menggambungkan baris dari dua tabel berdasarkan kesamaan nilai kolom yang dijadikan kondisi JOIN. Hanya baris yang memiliki kesamaan nilai dalam kedua tabel yang akan dihasilkan.
2. LEFT JOIN ( atau LEFT OUTER JOIN): Menggambungkan baris dari dua tabel berdasarkan kesamaan nilai dalam kolom yang dijadikan kondisi JOIN. Selain itu, semua beris dari tabel yang di-left join akan tetap ditampilkan, bahkan jika tidak ada kesamaan nilai dalam tabel kanan.
3. RIGHT JOIN (atau RIGHT OUTER JOIN): Mirip dengan LEFT JOIN, tetapi semua baris dari tabel yang di-right join akan tetap ditampilkan, bahkan jika tidak ada kesamaan nilai dalam tabel kiri.
4. FULL JOIN (atau FULL OUTER JOIN): Menggabungkan baris dari dua tabel dengan mempertahankan semua baris dari kedua tabel, bahkan jika tidak ada kesamaan nilai. Jika tidak ada kesamaan nilai, kolom untuk tabel yang tidak memiliki nilai akan berisi NULL.
5. CROSS JOIN: Menghasilkan hasil gabungan dari kedua tabel tanpa memerikaa kondisi. Jumlah baris yang dihasilkan akan menjadi perkalian dari jumlah baris pada kedua tabel.

## **LATIHAN**

- Lakukan join table Mahasiswa dan Dosen
- Lakukan join table Matakuliah dan Dosen
- Lakukan join table JadwalMengajar, Dosen, dan Matakuliah
- Lakukan join table KrsMahasiswa, Mahasiswa, Matakuliah dan Dosen

## **TUGAS PRAKTIKUM**

[1. Buat Script SQL JOIN Table berdasarkan skema data diatas]  
[2. Buat laporan praktikum yang berisi, langkah-langkah praktikum beserta screeenshot yang sudah dilakukan dalam bentuk dokumen]

### **SCRIPT SQL-JOIN**

1. JOIN table Mahasiswa dan Dosen
   ```sql
   SELECT mahasiswa.nim, mahasiswa.nama, mahasiswa.jk, dosen.nama, AS 'Dosen_PA'
   FROM mahasiswa
   INNER JOIN dosen ON dosen.kd_ds = mahasiswa.kd_ds;
   ```
2. JOIN Table Matakuliah, Jadwal_mengajar dan Dosen
   ```sql
   SELECT jadwal_mengajar.kd_mk, matakuliah.nama, matakuliah.sks, dosen.nama as Dosen_Pengampu
   FROM jadwal_mengajar
   INNER JOIN matakuliah ON jadwal_mengajar.kd_mk = matakuliah.kd_mk
   INNER JOIN dosen ON jadwal_mengajar.kd_ds = dosen.kd_ds;
   ```
3. LEFT JOIN Table Mahasiswa dan Dosen
   ```sql
   SELECT * mahasiswa.nim, mahasiswa.nama, mahasiswa.jk, dosen.nama AS Dosen_PA
   FROM mahasiswa
   LEFT JOIN dosen ON dosen.kd_ds = mahasiswa.kd_ds;
   ```
4. JOIN table Jadwal Mengajar, Dosen, dan Matakuliah
   ```sql
   SELECT jadwal_mengajar.kd_mk, matakuliah.nama, matakuliah.sks, dosen.nama AS Dosen_Pengampu
   FROM jadwal_mengajar
   INNER JOIN matakuiah ON matakuliah.kd_mk = jadwal_mengajar.kd_mk
   INNER JOIN dosen ON dosen.kd_ds = jadwal_mengajar.kd_ds;
   ```
5. JOIN table KrsMahasiswa, Mahaiswa, Matakuliah dan Dosen
   ```sql
   SELECT krsmahasiswa.nim, mahasiswa.nama, dosen1.nama AS 'Dosen PA', matakuliah.nama AS Matakuliah, matakuliah.sks, dosen2.nama AS 'Dosen Pengampu'
   FROM krsmahasiswa
   INNER JOIN mahasiswa ON krsmahasiswa.nim = mahasiswa.nim
   LEFT JOIN dosen AS dosen1 ON krsmahasiswa.kd_ds = dosen1.kd_ds
   INNER JOIN matakuliah ON krsmahasiswa.kd_mk = matakuliah.kd_mk
   LEFT JOIN dosen AS dosen2 ON dosen2.kd_ds = krsmahasiswa.kd_ds
   ```

### **KESIMPULAN**

1. Join antara tabel "Mahasiswa" dan "Dosen":
   - Digunakan untuk menghubungkan mahasiswa dengan dosen yang menjadi pembimbingnya.
   - Data yang dihubungkan adalah kolom "kd_ds" pada tabel "Mahasiswa" dan "kd_ds" pada tabel "Dosen".
2. Join antara tabel "Matakuliah" dan "Dosen":
   - Digunakan untuk menghubungkan matakuliah dengan dosen pengajar yang bertanggung jawab.
   - Data yang dihubungkan adalah kolom "kd_ds" pada tabel "Matakuliah" dan "kd_ds" pada tabel "Dosen".
3. Join antara tabel "JadwalMengajar", "Dosen", dan "Matakuliah":
   - Digunakan untuk menghubungkan jadwal mengajar dengan dosen pengajar dan matakuliah yang diajar.
   - Data yang dihubungkan adalah kolom "kd_mk" pada tabel "JadwalMengajar", "kd_ds" pada tabel "JadwalMengajar" dan "Dosen", serta "kd_mk" pada tabel "Matakuliah".
4. Join antara tabel "KRSMahasiswa", "Mahasiswa", "Matakuliah", dan "Dosen":
   - Digunakan untuk menghubungkan KRS (Kartu Rencana Studi) mahasiswa dengan informasi mahasiswa, matakuliah, dan dosen pengajar.
   - Data yang dihubungkan adalah kolom "nim" pada tabel "KRSMahasiswa" dan "Mahasiswa", kolom "kd_mk" pada tabel "KRSMahasiswa" dan "Matakuliah", serta kolom "kd_ds" pada tabel "KRSMahasiswa" dan "Dosen".


