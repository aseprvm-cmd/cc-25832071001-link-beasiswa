# Requirements

## Problem Statement
Mahasiswa kesulitan menemukan informasi beasiswa yang valid dan masih
dibuka karena informasinya tersebar di banyak sumber. Sistem
menyediakan kumpulan tautan beasiswa yang dapat ditambahkan siapa pun,
lengkap dengan tenggat dan status, sehingga mahasiswa dapat menemukan
dan mendaftar tepat waktu. (ASUMSI; akan diverifikasi lewat wawancara
singkat dengan pengguna)

## Target Users
- Pengguna umum (mahasiswa): melihat, mencari, menambah, dan
  melaporkan beasiswa.
- Admin (lebih dari satu orang): memeriksa beasiswa yang dilaporkan,
  memulihkan atau menghapusnya. Admin berfungsi sebagai jaring
  pengaman, bukan pemeriksa setiap entri.

## User Needs
- Sebagai pengguna, saya ingin melihat daftar beasiswa yang masih
  dibuka beserta tenggatnya, sehingga saya tidak ketinggalan.
- Sebagai pengguna, saya ingin menambahkan tautan beasiswa yang saya
  temukan, sehingga teman-teman lain ikut terbantu.
- Sebagai pengguna, saya ingin melaporkan beasiswa yang mencurigakan,
  sehingga orang lain terlindungi dari informasi palsu.
- Sebagai admin, saya ingin memeriksa beasiswa yang dilaporkan,
  sehingga tautan palsu tidak terus tampil.

## Functional Requirements
- FR-01 Sistem menampilkan halaman utama. (M03)
- FR-02 Sistem menyediakan health endpoint `/health`. (M03)
- FR-03 Sistem menampilkan metadata aplikasi `/api/info`. (M03)
- FR-04 Sistem menampilkan daftar beasiswa dan dapat disaring menurut
  jenjang, diurutkan menurut tenggat. (M05)
- FR-05 Pengguna dapat menambahkan beasiswa (nama, penyelenggara,
  jenjang, tenggat, tautan) yang langsung tampil. (M05)
- FR-06 Pengguna dapat melaporkan beasiswa; beasiswa yang dilaporkan
  diberi tanda "dilaporkan pengguna". (M05)
- FR-07 Beasiswa yang dilaporkan oleh minimal 3 perangkat berbeda
  disembunyikan otomatis (angka 3 adalah usulan). (M05)
- FR-08 Admin dapat memulihkan atau menghapus beasiswa yang
  disembunyikan, dan tindakannya tercatat. (M05)

## Non-Functional Requirements
- NFR-01 Backend hanya listen pada loopback (127.0.0.1).
- NFR-02 Aplikasi dikelola oleh systemd.
- NFR-03 Request publik masuk melalui reverse proxy.
- NFR-04 Secret tidak disimpan pada Git repository.
- NFR-05 Health endpoint mengembalikan HTTP 200 saat sehat.
- NFR-06 Deployment dapat direproduksi dari repository.
- NFR-07 Arsitektur sesuai VPS dengan RAM 1 GB.
- NFR-08 Data pengguna dibatasi seminimal mungkin; informasi beasiswa
  ditampilkan sebagai "dikirim pengguna, belum diverifikasi".

## Scope
### In Scope M03
Repository, requirements, architecture, ADR, baseline Flask app,
SSH hardening dasar, Gunicorn, systemd, Caddy, HTTP public deployment.

### Out of Scope M03
Fitur beasiswa (FR-04 sampai FR-08, direncanakan M05), database
production, Docker, Infrastructure as Code, CI/CD, TLS/domain
production, horizontal scaling, monitoring stack penuh, notifikasi.

## Constraints
- 2 vCPU (hasil `nproc`), 1 GB RAM, disk 29 GB (hasil `df`)
- Ubuntu Server 24.04 LTS
- Public IPv4

## Acceptance Criteria M03
- [x] First deployment dapat diakses publik
- [x] Health endpoint mengembalikan HTTP 200
- [ ] Evidence tersedia di docs/evidence/m03
