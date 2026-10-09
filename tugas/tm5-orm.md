# TM-5: Analisis ORM dan Keamanan Query

Dokumen ini menyajikan analisis perbandingan antara eksekusi perintah database menggunakan **Raw SQL Query** dan **Object-Relational Mapping (ORM)**, serta dampaknya terhadap keamanan aplikasi dari celah **SQL Injection**.

---

## 1. Perbandingan Kode: Menghitung Total Jadwal

### A. Pendekatan Raw SQL (MySQL Drive / `mysql2`)
```javascript
// Menggunakan query string SQL langsung
const [rows] = await db.query('SELECT COUNT(*) AS total FROM jadwal');
const totalJadwal = rows[0].total;

// Menggunakan metode/fungsi yang disediakan oleh ORM
const totalJadwal = await prisma.jadwal.count();

ParameterRaw | SQL Query | ORM (Prisma / Sequelize)
Kemudahan Penulisan |	Membutuhkan sintaks SQL manual yang rapi.	| Lebih intuitif menggunakan metode JavaScript biasa.
Sintaks & Abstraksi |	Terikat erat dengan dialek database tertentu (misal: MySQL). |	Bebas dialek DB (mudah migrasi dari MySQL ke PostgreSQL/SQLite).
Performa |	Sangat tinggi (eksekusi langsung tanpa layer abstraksi). |	Sedikit lebih berat karena ada proses penterjemahan query oleh ORM.
Keamanan (SQL Injection) |	Rentan jika menggunakan perangkaian string (string concatenation). |	Aman secara bawaan (secure by default) karena menggunakan parameterized queries

// SANGAT RENTAN SQL INJECTION!
const status = req.query.status; // Input user misal: "aktif' OR '1'='1"
const query = `SELECT * FROM jadwal WHERE status = '${status}'`;

SELECT * FROM jadwal WHERE status = 'aktif' OR '1'='1';

const status = req.query.status;
const data = await prisma.jadwal.findMany({
  where: { status: status }
});

