# Tainted Shadow Team – Setup & Workflow

Repo ini disiapkan dengan cabang per anggota dan alur kerja aman tanpa force push.

## Cabang Anggota
- `andhika`
- `nuafuddin`
- `aris`
- `raditya`
- `irfan`
- `radyasena`

`main` adalah cabang stabil; semua perubahan masuk lewat Pull Request (PR).

## Persiapan Lokal
1) Install Git dan Git LFS (sekali saja):
   ```bash
   git lfs install
   ```
2) Clone repo (contoh):
   ```bash
   git clone <url_repo_github>
   cd <folder_repo>
   ```
3) Pindah ke cabang masing‑masing:
   ```bash
   git switch <namacabangmu>
   ```

## Aturan Kerja Harian (tanpa force)
- Commit kecil dan jelas di cabang masing‑masing.
- Secara berkala sinkronkan dari `main` ke cabangmu (tanpa rebase agar tidak perlu force):
  ```bash
  git fetch origin
  git switch <namacabangmu>
  git merge origin/main     # gabungkan perubahan terbaru dari main
  ```
- Jika ada konflik, selesaikan lokal, test, lalu `git add` dan `git commit`.
- Push perubahanmu:
  ```bash
  git push -u origin <namacabangmu>
  ```

## Membuat Pull Request
1) Push cabangmu ke GitHub.
2) Buka GitHub → pilih *Compare & pull request*.
3) Target PR: `main` ← `<namacabangmu>`.
4) Minta minimal 1 review dari leader/teman.
5) Setelah disetujui, *Merge* (gunakan *Create a merge commit*). Tanpa squash/rebase untuk pemula agar riwayat tetap mudah.

## Menghindari Konflik
- Hindari mengedit file asset yang sama bersamaan; saling koordinasi.
- Gunakan Git LFS untuk `.uasset/.umap/.fbx/.wav/.mp3` (sudah dikonfigurasi).
- Jangan commit folder build/cache: `Binaries/`, `Build/`, `DerivedDataCache/`, `Intermediate/`, `Saved/` (sudah di‑ignore).
- Sering lakukan `git merge origin/main` di cabangmu sebelum lanjut kerja.

## Proteksi `main` (di GitHub – dilakukan leader)
- Settings → Branches → *Branch protection rules*.
- Tambahkan rule untuk `main`:
  - Centang “Require a pull request before merging”.
  - Centang “Require approvals” (misal 1 approval).
  - Centang “Do not allow bypassing the above settings”.
  - Nonaktifkan *force pushes* di `main`.

## Cheat Sheet Perintah
- Ganti cabang: `git switch <branch>`
- Lihat status: `git status`
- Commit: `git add . && git commit -m "pesan"`
- Sinkron dari main: `git fetch origin && git merge origin/main`
- Push: `git push -u origin <branch>`

Selamat bekerja! Bila butuh branch tambahan, buat dengan format sederhana (misal `andhika-ui`, `aris-ai`) lalu PR ke `main`.