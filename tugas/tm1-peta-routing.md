# TM-1: Peta Routing (Domain: Kamar Hotel)

Dokumen ini berisi rancangan peta routing RESTful API untuk entitas **Kamar** pada sistem manajemen hotel.

## Tabel Peta Routing

| Method | Endpoint URL | Asal Input | Status Sukses | Status Gagal | Deskripsi / Tujuan |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **GET** | `/api/v1/kamar` | `req.query` (`?tipe=`) | `200 OK` | `500 Internal Server Error` | Menampilkan seluruh daftar kamar (dapat difilter berdasarkan tipe) |
| **GET** | `/api/v1/kamar/:id` | `req.params.id` | `200 OK` | `400 Bad Request`, `404 Not Found` | Mengambil detail 1 kamar berdasarkan ID kamar |
| **POST** | `/api/v1/kamar` | `req.body` (JSON) | `201 Created` | `400 Bad Request` | Menambahkan unit kamar baru ke sistem |
| **PUT** | `/api/v1/kamar/:id` | `req.params.id` & `req.body` | `200 OK` | `400 Bad Request`, `404 Not Found` | Memperbarui data/status kamar berdasarkan ID |
| **DELETE** | `/api/v1/kamar/:id` | `req.params.id` | `200 OK` | `400 Bad Request`, `404 Not Found` | Menghapus data kamar dari sistem |

## Contoh Format Request & Response Body

### 1. POST /api/v1/kamar
**Request Body:**
```json
{
  "nomorKamar": "101",
  "tipe": "Deluxe",
  "harga": 500000,
  "status": "tersedia"
}

{
  "status": true,
  "message": "Kamar berhasil ditambahkan",
  "data": {
    "id": 1,
    "nomorKamar": "101",
    "tipe": "Deluxe",
    "harga": 500000,
    "status": "tersedia"
  }
}

{
  "status": "terisi"
}

{
  "status": true,
  "message": "Data kamar berhasil diperbarui",
  "data": {
    "id": 1,
    "nomorKamar": "101",
    "tipe": "Deluxe",
    "harga": 500000,
    "status": "terisi"
  }
}