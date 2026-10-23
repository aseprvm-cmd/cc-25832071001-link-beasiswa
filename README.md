# Sistem Praktikum dan Peminjaman Alat Lab

Cloud Computing - PTI 2802
Pertemuan 3 - Project Inception

## Author
Asep Solihin / NIM 25832071001 / Kelas PTI 2A

## Problem
Pencatatan peminjaman alat dan kegiatan praktikum lab masih manual
sehingga alat sulit dilacak dan hasil belajar mahasiswa tidak terekam.

## Target Users
Administrator lab, mahasiswa, dosen/kepala lab.

## Features M03
- Baseline aplikasi Flask
- Health endpoint
- First VPS deployment

## Planned Features
- Daftar praktikum, sesi, dan alat lab
- Peminjaman dan pengembalian alat per sesi
- Logbook praktikum mahasiswa

## Architecture

```mermaid
flowchart LR
    U[User] --> C[Caddy]
    C --> G[Gunicorn]
    G --> F[Flask]
```

## Infrastructure
- Ubuntu Server 24.04, 2 vCPU, 1 GB RAM, 29 GB disk
- Caddy, Gunicorn, systemd, UFW

## Public Endpoint
`http://85.211.252.8/`

## Health Check
`GET /health`

## Deployment
Lihat `docs/deployment.md`.

## Security
- SSH key-only, root SSH dinonaktifkan
- UFW aktif
- Backend loopback-only

## Current Limitations
- HTTP only
- Belum ada database
- Belum ada container
- Deployment manual

## Roadmap
M04 DNS/HTTPS, M05 Data (praktikum, alat, logbook), M06 Container,
M07 IaC, M09 CI/CD