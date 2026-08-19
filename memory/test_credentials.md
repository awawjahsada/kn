# Kredensial Uji — Kain Nusantara (WMS/ERP)

> Berkas ini **di-.gitignore**, jadi ia HILANG setiap clone dan harus ditulis ulang.
> Ditulis ulang: sesi 2026-08-19 (FASE T — Tahapan Proses & Screen).

## Sandi
Semua akun demo memakai sandi yang sama: **`demo12345`**

## Login API
`POST /api/auth/login` body `{"email": "...", "password": "demo12345"}`
→ respons memakai key **`token`** (BUKAN `access_token`).
Header badan usaha aktif: **`X-Entity-Id: ent_ksc | ent_kanda | all`**
(`all` = mode gabungan **hanya-lihat**; membuat dokumen baru di mode ini ditolak 409
oleh pagar tulis `backend/entity_write_guard.py` — itu memang disengaja).

## Akun (domain `@kainnusantara.id`)
| Email | Peran | Badan usaha (home) | Catatan |
|---|---|---|---|
| `admin@` | admin | PT Kain Suka Cita (`ent_ksc`) | Budi Santoso — akses penuh, dipakai POC |
| `manager@` | manager | `ent_ksc` | Dewi Rahayu — persetujuan klaim/harga |
| `adminsales.lama@` | manager | `ent_ksc` | Rudi Hartono |
| `sales@` | sales | `ent_ksc` | Ayu Permatasari |
| `sales2@` | sales | `ent_ksc` | Bima Saputra |
| `sales3@` | sales | **CV Kanda Suka (`ent_kanda`)** | Citra Lestari — untuk uji isolasi antar badan usaha |
| `salesadmin@` | sales_admin | `ent_ksc` | Rina Kusumawati |
| `dewi.printing@` | sales | `ent_ksc` | Dewi Anggraini — **berpagar lini `printing`** (FASE L) |
| `warehouse@` | warehouse | `ent_ksc` | Eko Prasetyo — issue/terima hasil makloon |
| `warehouse2@` | warehouse | `ent_ksc` | Fitri Handayani |
| `finance@` | finance | `ent_ksc` | Hendra Wijaya |

## Jebakan yang sering menjatuhkan agen uji
1. **Tidak ada hash routing.** Navigasi berbasis state lewat sidebar:
   klik `nav-group-{groupId}` lalu `nav-{id}`. Satu-satunya jalur URL sungguhan:
   `/verify-document/:id`. `#/view` **bukan** navigasi aplikasi ini.
2. **Pelanggan `Toko Kain Sejahtera` diblokir kredit** (gate lama). Untuk membuat
   pesanan pakai *Butik Bali Indah* / *Fashion Bandung Kencana* / *Tekstil Medan Jaya*.
3. **Preview dilayani dari `frontend/build/`** yang di-.gitignore → setelah clone,
   layar kosong sampai `bash scripts/rebuild_frontend.sh` dijalankan.
4. Jangan menimpa berkas uji milik repo (`backend/backend_test*.py`). Skrip agen uji
   pakai nama sendiri.
5. Nomor demo yang dipakai POC FASE T: SPK **MKO-00001/2/3** (sebelum FASE T),
   **MKO-00004** (pre-treatment → SCREEN → printing) dan **MKO-00005** (menyisakan
   24,5 yard PFP di gudang untuk mencoba Screen dari layar).
