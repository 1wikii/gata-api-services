# 🎓 GATA API Services

> **REST API untuk Sistem Manajemen Proyek Akhir Mahasiswa**
>
> Platform komprehensif untuk mengelola seluruh siklus proyek akhir/skripsi mahasiswa dari perencanaan hingga evaluasi.

---

## ✨ Fitur Utama

### 👥 Manajemen Pengguna & Role-Based Access

- **Multiple Role Support**: Admin, Lecturer (Dosen), Student (Mahasiswa)
- **Autentikasi Aman**: JWT Token + Google OAuth 2.0
- **Profil Pengguna**: Manajemen data lengkap pengguna dengan role spesifik
- **Dashboard Khusus**: Setiap role memiliki dashboard dengan metrics relevan

### 📋 Manajemen Proyek Akhir

- **Periode Proyek**: Kelola periode/tahun akademik untuk proyek akhir
- **Pendaftaran Anggota**: Sistem manage member tim proyek
- **Tracking Status**: Monitor progress dan status proyek secara real-time
- **Export Data**: Generate laporan dalam format CSV

### 👨‍🏫 Sistem Bimbingan

- **Jadwal Bimbingan**: Kelola ketersediaan dan slot bimbingan dosen
- **Sesi Bimbingan**: Catat dan track sesi bimbingan yang telah dilakukan
- **Draft & Revisi**: Kelola link draft dan revisi dari mahasiswa
- **Notifikasi**: Sistem notifikasi untuk reminder dan update

### 🏆 Sistem Penilaian & Evaluasi

- **Rubrik Penilaian**: Buat dan kelola rubrik penilaian multi-level
- **Skala Penilaian**: Tentukan rentang nilai untuk setiap criteria
- **Pertanyaan & Jawaban**: Bank soal untuk evaluasi proyek
- **Opsi Jawaban**: Multi-choice untuk penilaian terstruktur

### 📅 Manajemen Sidang/Defense

- **Jadwal Sidang**: Atur dan publish jadwal sidang/defense
- **Submission Management**: Terima dan validasi dokumen submission
- **Berita Acara PDF**: Generate otomatis berita acara dalam format PDF
- **Tanda Tangan Digital**: Sistem signature untuk dokumen resmi

### 📢 Sistem Notifikasi & Komunikasi

- **Email Service**: Pengiriman notifikasi via email otomatis
- **Announcement**: Post pengumuman global untuk semua pengguna
- **Notification Center**: Notifikasi real-time untuk sistem penting

### 🎯 Fitur Tambahan

- **Keahlian Dosen**: Manajemen expertise dan spesialisasi dosen
- **Export Berita Acara**: Generate BAP (Berita Acara Penilaian) PDF
- **Cron Jobs**: Scheduled tasks untuk proses otomatis
- **Rate Limiting**: Proteksi API dari abuse
- **File Storage**: Kelola penyimpanan file upload (PDF, dokumen, dll)

---

## 🛠️ Tech Stack

```
Backend Framework:     Express.js (TypeScript)
Database:             MySQL / SQLite
ORM:                  TypeORM
Authentication:       JWT + Passport.js (Google OAuth)
File Processing:      Multer, PDF-lib, Puppeteer
Scheduling:           Node-cron
Email:                Nodemailer
API Documentation:    Swagger/OpenAPI
Security:             Helmet, CORS, Rate Limiting
Validation:           Class-validator, Express-validator
```

---

## 📁 Struktur Project

```
src/
├── config/              # Konfigurasi database, swagger, google oauth
├── controllers/         # Logic handler per endpoint
│   ├── admin/
│   ├── auth/
│   ├── lecturer/
│   └── student/
├── entities/            # Data models (TypeORM)
├── repositories/        # Data access layer (23+ repositories)
├── services/            # Business logic layer
├── routes/              # API endpoints routing
├── middleware/          # Auth, validation, file upload
├── jobs/                # Scheduled tasks & cron jobs
├── migrations/          # Database migrations
├── seeds/               # Database seeding
├── types/               # TypeScript interfaces & types
├── utils/               # Helper functions
└── swagger/             # API documentation
```

---

## 🚀 Instalasi & Setup

### Prerequisites

- Node.js (v14+)
- MySQL atau SQLite
- npm atau yarn

### Installation

```bash
# Clone repository
git clone <repository-url>
cd gata-api-services

# Install dependencies
npm install

# Setup environment variables
cp .env.example .env
# Edit .env dengan konfigurasi database Anda

# Database migrations
npm run migrate:fresh

# Seed database (optional)
npm run seed
npm run seed:dummy
```

### Running Application

```bash
# Development mode (dengan hot reload)
npm run dev

# Production build
npm run build
npm run prod

# Verify build
npm run verify
```

---

## 📊 API Endpoints Overview

### Authentication

- `POST /auth/register` - Registrasi pengguna baru
- `POST /auth/login` - Login dengan email/password
- `GET /auth/google` - Login dengan Google OAuth
- `POST /auth/logout` - Logout

### Student Routes

- `GET /student/dashboard` - Dashboard mahasiswa
- `GET /student/projects` - List proyek mahasiswa
- `POST /student/projects` - Daftar proyek baru
- `GET /student/guidance` - History bimbingan

### Lecturer Routes

- `GET /lecturer/dashboard` - Dashboard dosen
- `POST /lecturer/availability` - Atur jadwal bimbingan
- `GET /lecturer/students` - List mahasiswa bimbingan
- `POST /lecturer/assessment` - Submit penilaian

### Admin Routes

- `GET /admin/dashboard` - Dashboard admin
- `POST /admin/period` - Buat periode baru
- `GET /admin/reports` - Generate reports
- `POST /admin/announcements` - Post pengumuman

### General

- `GET /jadwal-sidang` - Get jadwal defense/sidang
- `GET /swagger` - Dokumentasi API (Swagger UI)

---

## 🔐 Security Features

✅ **JWT Authentication** - Token-based secure access  
✅ **Helmet.js** - HTTP headers protection  
✅ **CORS Configuration** - Cross-origin resource sharing control  
✅ **Rate Limiting** - Prevent brute force attacks  
✅ **Password Hashing** - Bcrypt encryption  
✅ **Input Validation** - Server-side validation untuk semua input  
✅ **Role-Based Access Control** - Middleware untuk autorization

---

## 📝 Environment Variables

```env
PORT=5000
NODE_ENV=development

# Database
DB_HOST=localhost
DB_PORT=3306
DB_USERNAME=root
DB_PASSWORD=password
DB_DATABASE=gata_db
DB_TYPE=mysql

# JWT
JWT_SECRET=your-secret-key
JWT_EXPIRE=24h

# Google OAuth
GOOGLE_CLIENT_ID=your-client-id
GOOGLE_CLIENT_SECRET=your-client-secret

# Email Service
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USER=your-email@gmail.com
MAIL_PASS=your-app-password

# API
API_URL=http://localhost:5000
FRONTEND_URL=http://localhost:3000
```

---

## 📑 Dokumentasi API

Dokumentasi lengkap API tersedia di:

```
http://localhost:5000/api/swagger
```

Gunakan Swagger UI untuk explore dan test semua endpoints dengan mudah.

---

## 📦 Database Entities

- **User** - Pengguna sistem (base entity)
- **Student** - Data mahasiswa
- **Lecturer** - Data dosen/pembimbing
- **FinalProject** - Proyek akhir
- **FinalProjectMember** - Anggota tim proyek
- **DefenseSchedule** - Jadwal sidang
- **Defense** - Data sidang/defense
- **Guidance** - Sesi bimbingan
- **Penilaian** - Penilaian project
- **Rubrik** - Kriteria penilaian
- **Notification** - Notifikasi sistem
- **Announcement** - Pengumuman
- Dan lebih banyak lagi...

---

## 🤝 Kontribusi

Untuk berkontribusi pada project ini:

1. Fork repository
2. Buat branch fitur (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buat Pull Request

---

## 📄 Lisensi

Distributed under the MIT License. See `LICENSE` file for more information.

---

## 📧 Support & Contact

Untuk pertanyaan atau support:

- Email: support@gata.ac.id
- Issue Tracker: Buka issue di repository

---

**Made with ❤️ by GATA Development Team**
