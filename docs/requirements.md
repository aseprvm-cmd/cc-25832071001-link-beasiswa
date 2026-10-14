# Requirements

## Problem Statement
Administrator dan mahasiswa laboratorium kesulitan melacak peminjaman
perangkat lab karena pencatatan masih manual dan tidak terpusat.
Sistem menyediakan pencatatan perangkat, peminjaman, dan status
pengembalian sehingga penggunaan perangkat dapat ditelusuri.

## Target Users
- Administrator lab: mengelola data perangkat dan peminjaman.
- Mahasiswa peminjam: mengajukan dan melihat status peminjaman.
- Dosen/Kepala lab: memantau penggunaan perangkat.

## User Needs
- Sebagai administrator, saya ingin melihat perangkat yang belum
  dikembalikan, sehingga saya dapat menindaklanjuti keterlambatan.
- Sebagai mahasiswa, saya ingin melihat perangkat yang tersedia,
  sehingga saya tidak perlu bertanya langsung ke petugas.
- Sebagai kepala lab, saya ingin riwayat peminjaman, sehingga
  penggunaan perangkat dapat diaudit.

## Functional Requirements
- FR-01 Sistem menampilkan halaman utama. (M03)
- FR-02 Sistem menyediakan health endpoint `/health`. (M03)
- FR-03 Sistem menampilkan metadata aplikasi `/api/info`. (M03)
- FR-04 Sistem menampilkan daftar perangkat lab. (M05)
- FR-05 Sistem mencatat peminjaman dan pengembalian perangkat. (M05)

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
TLS/domain production, horizontal scaling, monitoring stack penuh.

## Constraints
- 2 vCPU (hasil `nproc`), 1 GB RAM, disk 29 GB (hasil `df`)
- Ubuntu Server 24.04 LTS
- Public IPv4

## Acceptance Criteria M03
- [x] First deployment dapat diakses publik
- [x] Health endpoint mengembalikan HTTP 200
- [ ] Evidence tersedia di docs/evidence/m03
