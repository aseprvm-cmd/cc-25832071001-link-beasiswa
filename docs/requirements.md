# Requirements

## Problem Statement
Administrator, dosen, dan mahasiswa laboratorium kesulitan melacak
peminjaman alat lab serta kegiatan praktikum yang menggunakannya karena
pencatatan masih manual dan tidak terpusat. Sistem menyediakan pencatatan
praktikum, sesi, peminjaman alat per sesi, dan logbook mahasiswa sehingga
penggunaan alat dan hasil belajar dapat ditelusuri.

## Target Users
- Administrator lab: mengelola data alat, praktikum, sesi, dan peminjaman.
- Mahasiswa: mendaftar sesi, meminjam alat, dan mengisi logbook praktikum.
- Dosen/Kepala lab: memantau keaktifan praktikum dan penggunaan alat.

## User Needs
- Sebagai administrator, saya ingin melihat alat yang belum dikembalikan,
  sehingga saya dapat menindaklanjuti keterlambatan.
- Sebagai mahasiswa, saya ingin melihat alat yang tersedia dan sesi
  praktikum yang dibuka, sehingga saya tidak perlu bertanya langsung
  ke petugas.
- Sebagai mahasiswa, saya ingin mengisi logbook setiap praktikum,
  sehingga saya memiliki catatan hasil belajar sendiri.
- Sebagai dosen/kepala lab, saya ingin melihat progres praktikum dan
  riwayat peminjaman, sehingga kegiatan lab dapat diaudit.

## Functional Requirements
- FR-01 Sistem menampilkan halaman utama. (M03)
- FR-02 Sistem menyediakan health endpoint `/health`. (M03)
- FR-03 Sistem menampilkan metadata aplikasi `/api/info`. (M03)
- FR-04 Sistem menampilkan daftar praktikum, sesi, dan alat lab. (M05)
- FR-05 Sistem mencatat peminjaman dan pengembalian alat per sesi
  praktikum. (M05)
- FR-06 Sistem menyimpan logbook mahasiswa per sesi praktikum. (M05)

## Non-Functional Requirements
- NFR-01 Backend hanya listen pada loopback (127.0.0.1).
- NFR-02 Aplikasi dikelola oleh systemd.
- NFR-03 Request publik masuk melalui reverse proxy.
- NFR-04 Secret tidak disimpan pada Git repository.
- NFR-05 Health endpoint mengembalikan HTTP 200 saat sehat.
- NFR-06 Deployment dapat direproduksi dari repository.
- NFR-07 Arsitektur sesuai VPS dengan RAM 1 GB.

## Scope

### In Scope M03
Repository, requirements, architecture, ADR, baseline Flask app,
SSH hardening dasar, Gunicorn, systemd, Caddy, HTTP public deployment.

### Out of Scope M03
Database production, Docker, Infrastructure as Code, CI/CD,
TLS/domain production, horizontal scaling, monitoring stack penuh,
fitur praktikum dan logbook (direncanakan M05).

## Constraints
- 2 vCPU (hasil `nproc`), 1 GB RAM, disk 29 GB (hasil `df`)
- Ubuntu Server 24.04 LTS
- Public IPv4

## Acceptance Criteria M03
- [x] First deployment dapat diakses publik
- [x] Health endpoint mengembalikan HTTP 200
- [x] Evidence tersedia di docs/evidence/m03