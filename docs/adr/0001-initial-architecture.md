# ADR-0001: Initial VPS Deployment Architecture

## Status
Accepted

## Context
Proyek Sistem Pengumpulan Tautan Beasiswa membutuhkan deployment
publik yang aman, sederhana, dan dapat direproduksi dari repository.
Beban aplikasi didominasi pembacaan daftar tautan. VPS Ubuntu Server
24.04 memiliki RAM 1 GB (2 vCPU terdeteksi) dan disk 29 GB.

## Decision
- Flask sebagai web framework
- Gunicorn (1 worker, 2 thread) sebagai application server
- systemd sebagai service manager
- Caddy sebagai reverse proxy
- UFW sebagai host firewall
- GitHub sebagai remote repository dengan deploy key

## Alternatives
1. Node.js + PM2
2. NGINX + Gunicorn
3. Docker
4. PHP-FPM

## Rationale
- Python 3.12 sudah menjadi runtime default Ubuntu 24.04.
- Gunicorn dapat di-bind ke loopback sehingga backend tidak terekspos.
- Caddy konfigurasinya ringkas dan siap HTTPS otomatis pada M04.
- Satu worker menjaga headroom RAM untuk SSH, systemd, dan Caddy.
- Docker ditunda karena containerization menjadi capaian M06.

## Consequences
### Positive
- Footprint kecil, sesuai RAM 1 GB
- Attack surface kecil (hanya port 22 dan 80)
- Mudah dipahami dan di-troubleshoot

### Negative
- Throughput terbatas (1 worker)
- Deployment masih manual
- HTTP only sampai M04

## Review Trigger
Review pada M06/M07.
