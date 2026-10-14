# Evidence Notes M03

- Tanggal pengerjaan: 12-14 Oktober 2026
- VPS: Azure VM, Ubuntu Server 24.04.5 LTS
- Resource terdeteksi: 2 vCPU (`nproc`), RAM 836 MiB, disk 29 GB
  (modul mengasumsikan 1 vCPU; konfigurasi Gunicorn tetap 1 worker
  sesuai ADR-0001 untuk menjaga headroom RAM)
- Swap 1 GB aktif lewat /etc/fstab
- Sistem diperbarui dengan `apt full-upgrade` (8 paket, 5 security)
- Reboot test: cc-m03 dan caddy `active` otomatis, UFW aktif,
  swap aktif, /health mengembalikan status ok
- Pengujian eksternal: `curl.exe -I http://85.211.252.8/` -> HTTP 200,
  header `Server: gunicorn` dan `Via: 1.1 Caddy`
- Browser: halaman utama, /health, dan /api/info dapat dibuka
