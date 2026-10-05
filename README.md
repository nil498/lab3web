# Laporan Praktikum 3: CSS Dasar

**Mata Kuliah:** Pemrograman Web
**Nama:** Daniel Mohammed
**NIM:** 312510466
**Kelas:** I251B
**Program Studi:** Teknik Informatika, Universitas Pelita Bangsa

---

## Struktur Repository

```
Lab3Web/
├── lab2_css_dasar.html     # dokumen HTML (berisi CSS internal + inline)
├── style_eksternal.css     # file CSS eksternal
├── README.md               # laporan ini
└── screenshots/            # tangkapan layar setiap langkah
```

---

## Langkah 1: Membuat Dokumen HTML

Pertama saya membuat file baru bernama `lab2_css_dasar.html` di VSCode, lalu mengisinya dengan struktur dasar HTML dari modul: ada `<header>` berisi judul `<h1>`, `<nav>` berisi tiga tautan, dan `<div id="intro">` berisi judul, paragraf, serta tautan bertombol dengan `class="button btn-primary"`. Saat dibuka di browser, tampilannya masih polos karena belum ada CSS sama sekali.

![Langkah 1](screenshots/01-html-dasar.png)
<img width="1920" height="1080" alt="Screenshot (122)" src="https://github.com/user-attachments/assets/77bcc371-56c3-449e-b8a6-064aa7728b41" />


## Langkah 2: Mendeklarasikan CSS Internal

CSS internal ditulis di dalam tag `<style>` pada bagian `<head>`. Saya menambahkan aturan untuk `body`, `header`, `h1`, dan `h1 i`:

```html
<style>
    body { font-family: 'Open Sans', sans-serif; }
    header { min-height: 80px; border-bottom: 1px solid #77CCEF; }
    h1 { font-size: 24px; color: #0F189F; text-align: center; padding: 20px 10px; }
    h1 i { color: #6d6a6b; }
</style>
```

Setelah disimpan dan browser di-refresh, semua judul menjadi biru, rata tengah, dan kata *Inline CSS* berwarna abu-abu karena kena aturan `h1 i`.

![Langkah 2](screenshots/02-css-internal.png)
<img width="1920" height="1080" alt="Screenshot (125)" src="https://github.com/user-attachments/assets/3bc39ce7-23df-46f2-b0a6-f069c932c178" />


## Langkah 3: Menambahkan Inline CSS

Inline CSS ditulis langsung sebagai atribut `style` pada tag HTML. Saya menambahkannya pada tag `<p>`:

```html
<p style="text-align: center; color: #ccd8e4;">
```

Paragraf jadi rata tengah dengan warna biru pucat. Aturan ini hanya berlaku untuk satu paragraf itu saja.

![Langkah 3](screenshots/03-inline-css.png)
<img width="1920" height="1080" alt="Screenshot (127)" src="https://github.com/user-attachments/assets/0e89147b-e01f-4477-b00f-cd7d40affd81" />


## Langkah 4: Membuat CSS Eksternal

Saya membuat file baru `style_eksternal.css` berisi aturan untuk `nav`, `nav a`, serta `nav .active` dan `nav a:hover`. Setelah itu file dihubungkan ke HTML memakai tag `<link>` di dalam `<head>`:

```html
<link rel="stylesheet" href="style_eksternal.css" type="text/css">
```

Hasilnya menu navigasi berubah menjadi bar hijau dengan teks putih tanpa garis bawah.

![Langkah 4](screenshots/04-css-eksternal.png)
<img width="1920" height="1080" alt="Screenshot (129)" src="https://github.com/user-attachments/assets/2249dbd2-d219-4fbd-bf2a-e6f390965399" />


## Langkah 5: Menambahkan CSS Selector (ID dan Class)

Pada `style_eksternal.css` saya menambahkan:

- **ID selector** `#intro` dan `#intro h1`, diawali tanda `#`. Pada HTML dipakai `id="intro"` tanpa tanda `#`. Satu id hanya boleh dipakai satu kali dalam satu halaman.
- **Class selector** `.button` dan `.btn-primary`, diawali tanda titik. Pada HTML dipakai `class="button btn-primary"` tanpa titik, dan satu elemen boleh punya lebih dari satu class.

Hasilnya kotak intro berwarna biru, judul "Hello World" putih rata kiri, dan tautan berubah menjadi tombol merah.

![Langkah 5](screenshots/05-id-class-selector.png)
<img width="1920" height="1080" alt="Screenshot (132)" src="https://github.com/user-attachments/assets/7de0a1ee-c9aa-48cc-93fb-71aa039ed6eb" />

## Langkah 6: Validasi CSS

File `style_eksternal.css` saya validasi lewat https://jigsaw.w3.org/css-validator/ (pilih tab *By file upload*, upload file CSS, lalu klik *Check*). Hasil yang diharapkan: tidak ada error.

---

## Jawaban Pertanyaan dan Tugas

### 1. Eksperimen mengubah dan menambah properti CSS

Saya menambahkan beberapa properti baru di `style_eksternal.css`:

```css
#intro {
    border-radius: 8px;                          /* sudut kotak melengkung */
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.25);  /* bayangan */
}
.button {
    border-radius: 6px;
    font-weight: bold;
}
.button:hover {
    background: #b01e32;                         /* warna tombol berubah saat kursor di atasnya */
}
```

Hasilnya kotak intro jadi melengkung dan punya bayangan, tombol menjadi tebal dan melengkung, serta warnanya lebih gelap saat kursor diarahkan ke tombol. Gambar 5 di atas sudah memakai properti-properti ini.

### 2. Perbedaan `h1 { ... }` dengan `#intro h1 { ... }`

- `h1 { ... }` adalah **selector elemen**. Aturannya berlaku untuk **semua** tag `<h1>` di halaman.
- `#intro h1 { ... }` adalah **selector turunan (descendant)** dengan ID. Aturannya hanya berlaku untuk `<h1>` yang berada **di dalam** elemen ber-`id="intro"`.

Karena `#intro h1` lebih spesifik, aturannya menang bila bentrok dengan `h1` biasa. Di praktikum ini terlihat jelas: `h1` di `<header>` tetap biru dan rata tengah (aturan `h1`), sedangkan `h1` "Hello World" di dalam `#intro` menjadi putih dan rata kiri (aturan `#intro h1`), padahal keduanya sama-sama tag `<h1>`.

### 3. Internal, eksternal, dan inline CSS pada elemen yang sama

Yang tampil di browser adalah **inline CSS**. Alasannya, inline punya prioritas tertinggi dibanding internal maupun eksternal.

Untuk internal dan eksternal, bobot (specificity) keduanya sama, sehingga yang menang adalah aturan yang **dibaca paling akhir** (prinsip *cascading*). Jadi bila `<link>` diletakkan **sebelum** `<style>`, internal yang menang. Bila `<link>` diletakkan **sesudah** `<style>`, eksternal yang menang.

Contoh:

```css
/* style_eksternal.css */
p { color: green; }
```
```html
<head>
    <link rel="stylesheet" href="style_eksternal.css">
    <style> p { color: red; } </style>
</head>
<body>
    <p style="color: blue;">Teks ini berwarna biru</p>
    <p>Teks ini berwarna merah</p>
</body>
```

Paragraf pertama **biru** (inline menang), paragraf kedua **merah** (internal menang karena ditulis setelah `<link>`). Urutan prioritasnya: **inline > internal/eksternal (yang terakhir dibaca)**. Pengecualian: deklarasi yang memakai `!important` mengalahkan inline sekalipun.

### 4. Elemen dengan ID dan Class sekaligus: `<p id="paragraf-1" class="textparagraf">`

Yang tampil adalah deklarasi **ID selector**, karena ID lebih spesifik daripada class. Bobot specificity: ID bernilai lebih tinggi dari class, dan class lebih tinggi dari selector elemen. Urutannya kira-kira: inline > ID > class > elemen.

Contoh:

```css
.textparagraf { color: red; }
#paragraf-1   { color: green; }
```
```html
<p id="paragraf-1" class="textparagraf">Paragraf ini berwarna hijau</p>
```

Paragraf berwarna **hijau**, walaupun `.textparagraf` ditulis lebih dulu atau lebih belakang. Hasilnya tidak bergantung pada urutan penulisan, karena bobot ID lebih besar. Properti yang tidak bentrok tetap digabung, misalnya bila class mengatur `font-size` dan ID mengatur `color`, kedua aturan itu tetap berlaku.

---
