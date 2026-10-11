# Lab3Web - Praktikum 3: CSS Dasar

Laporan Praktikum Pemrograman Web
Universitas Pelita Bangsa.

| | |
|---|---|
| **Nama** | _(Pahmi Dwika Fahlevi)_ |
| **NIM** | _(312510389)_ |
| **Kelas** | _(I253C)_ |
| **Dosen** | Agung Nugroho, S.Kom., M.Kom. |

---

## Tujuan

1. Memahami konsep dasar CSS.
2. Memahami aturan penulisan pada CSS.
3. Memahami selector sebagai pengontrol CSS.
4. Membuat pengaturan CSS pada HTML.

## Struktur Repository

```
Lab3Web/
├── lab2_css_dasar.html     # Dokumen HTML (CSS internal + inline + link eksternal)
├── style_eksternal.css     # File CSS eksternal
├── screenshots/            # Screenshot hasil tiap langkah
└── README.md
```

## Cara Menjalankan

1. Clone repository ini:
   ```bash
   git clone https://github.com/<username>/Lab3Web.git
   ```
2. Buka file `lab2_css_dasar.html` di browser (klik dua kali atau gunakan Live Server di VSCode).
3. Pastikan `style_eksternal.css` berada di folder yang sama dengan file HTML.

---

## Ringkasan Teori

**CSS (Cascading Style Sheet)** adalah aturan untuk mengatur tampilan komponen web agar lebih terstruktur dan seragam. Satu perubahan di file CSS akan berlaku di semua halaman yang memakainya.

Sebuah rule CSS terdiri dari dua komponen:

- **Selector**: menentukan elemen mana yang diberi style (elemen HTML, class, atau id).
- **Declaration**: aturan yang diterapkan, terdiri dari *property* dan *value*.

```css
h1 { color: blue; }
/* h1 = selector, color = property, blue = value */
```

**Tiga cara menulis CSS:**

| Cara | Penulisan | Cakupan |
|---|---|---|
| Internal | Tag `<style>` di dalam `<head>` | Satu dokumen HTML |
| Eksternal | File `.css` terpisah, dipanggil dengan `<link>` | Semua dokumen yang menautkannya |
| Inline | Atribut `style="..."` pada tag HTML | Satu elemen saja |

**Jenis selector:**

| Selector | Penulisan | Contoh |
|---|---|---|
| Elemen | nama tag | `p { color: green; }` |
| Class | diawali `.` | `.merah { color: red; }` → `<h1 class="merah">` |
| ID | diawali `#` | `#intro { ... }` → `<div id="intro">` |

Satu elemen boleh memiliki lebih dari satu class, tetapi hanya satu id.

---

## Langkah-langkah Praktikum

### 1. Membuat Dokumen HTML

Membuat file `lab2_css_dasar.html` berisi struktur dasar HTML: `<header>` dengan judul, `<nav>` dengan tiga link, dan `<div id="intro">` berisi judul, paragraf, serta tombol dengan class `button btn-primary`.

Pada tahap ini belum ada CSS, sehingga tampilan masih bawaan browser.


### 2. Mendeklarasikan CSS Internal

Menambahkan tag `<style>` di dalam `<head>` dengan aturan untuk `body`, `header`, `h1`, dan `h1 i`:

```html
<style>
    body {
        font-family: 'Open Sans', sans-serif;
    }
    header {
        min-height: 80px;
        border-bottom: 1px solid #77CCEF;
    }
    h1 {
        font-size: 24px;
        color: #0F189F;
        text-align: center;
        padding: 20px 10px;
    }
    h1 i {
        color: #6d6a6b;
    }
</style>
```

Hasil: font berubah menjadi Open Sans, judul menjadi biru, rata tengah, dan header diberi garis bawah. Teks miring di dalam `h1` berwarna abu-abu.


### 3. Menambahkan Inline CSS

Menambahkan atribut `style` pada tag `<p>`:

```html
<p style="text-align: center; color: #ccd8e4;">...</p>
```

Hasil: paragraf menjadi rata tengah dengan warna biru muda. Style ini hanya berlaku untuk paragraf tersebut.


### 4. Membuat CSS Eksternal

Membuat file `style_eksternal.css`:

```css
nav {
    background: #20A759;
    color: #fff;
    padding: 10px;
}
nav a {
    color: #fff;
    text-decoration: none;
    padding: 10px 20px;
}
nav .active,
nav a:hover {
    background: #0B6B3A;
}
```

Lalu menautkannya pada `<head>` di file HTML:

```html
<link rel="stylesheet" href="style_eksternal.css" type="text/css">
```

Hasil: menu navigasi berlatar hijau dengan link putih tanpa garis bawah. Saat kursor diarahkan ke link, latar berubah menjadi hijau lebih gelap.


### 5. Menambahkan CSS Selector (ID dan Class)

Menambahkan kode berikut pada `style_eksternal.css`:

```css
/* ID Selector */
#intro {
    background: #418fb1;
    border: 1px solid #099249;
    min-height: 100px;
    padding: 10px;
}
#intro h1 {
    text-align: left;
    border: 0;
    color: #fff;
}

/* Class Selector */
.button {
    padding: 15px 20px;
    background: #bebcbd;
    color: #fff;
    display: inline-block;
    margin: 10px;
    text-decoration: none;
}
.btn-primary {
    background: #E42A42;
}
```

Hasil: area `#intro` berlatar biru, judul "Hello World" menjadi putih dan rata kiri, dan link "Informasi selengkapnya." tampil sebagai tombol merah.


---

## Validasi CSS

File CSS divalidasi menggunakan W3C CSS Validator

---

## Pertanyaan dan Tugas

### 1. Eksperimen properti CSS

Saya mencoba mengubah dan menambah properti pada kode CSS, misalnya:

- _(tuliskan eksperimen kamu, contoh: mengubah `color`, menambah `border-radius` pada `.button`, mengubah `font-size`, dll.)_


### 2. Perbedaan `h1 {...}` dengan `#intro h1 {...}`

- `h1 {...}` adalah **selector elemen**: berlaku untuk **semua** tag `<h1>` di halaman.
- `#intro h1 {...}` adalah **selector turunan (descendant) berbasis ID**: hanya berlaku untuk `<h1>` yang berada **di dalam** elemen ber-`id="intro"`.

Selector kedua lebih spesifik, jadi jika keduanya mengatur properti yang sama, aturan `#intro h1` yang dipakai. Pada praktikum ini `h1` di header tetap biru dan rata tengah, sedangkan `h1` "Hello World" di dalam `#intro` menjadi putih dan rata kiri.

### 3. Prioritas CSS internal, eksternal, dan inline pada elemen yang sama

**Inline CSS** memiliki prioritas tertinggi dan akan ditampilkan browser. Internal dan eksternal berada di bawahnya. Jika selector keduanya sama-sama spesifik, yang **ditulis paling akhir** di dokumen yang dipakai. Misalnya, jika `<link>` eksternal diletakkan sebelum `<style>`, maka aturan internal yang menang.

Contoh:

```css
/* style_eksternal.css */
p { color: green; }
```
```html
<style>
    p { color: blue; }
</style>

<p style="color: red;">Teks ini berwarna merah</p>
```

Hasil: teks berwarna **merah** karena inline CSS mengalahkan internal (biru) dan eksternal (hijau).

Urutan prioritas: **Inline > Internal / Eksternal (sesuai urutan penulisan)**.

### 4. Prioritas ID dan Class pada satu elemen

**ID selector** memiliki prioritas lebih tinggi daripada class selector, karena spesifisitasnya lebih besar. Urutan spesifisitas: `elemen < class < id < inline`.

Contoh:

```css
.textparagraf { color: blue; }
#paragraf-1   { color: red; }
```
```html
<p id="paragraf-1" class="textparagraf">Paragraf ini berwarna merah</p>
```

Hasil: teks berwarna **merah**, karena deklarasi `#paragraf-1` mengalahkan `.textparagraf`, meskipun class ditulis lebih dulu atau lebih akhir.

---

## Kesimpulan

- CSS memisahkan tampilan dari struktur HTML sehingga perubahan style cukup dilakukan di satu tempat.
- Penulisan CSS bisa dilakukan secara internal, eksternal, dan inline, dengan inline berprioritas tertinggi.
- Selector elemen, class, dan id memiliki tingkat spesifisitas berbeda: elemen < class < id.
- CSS eksternal paling efisien untuk dipakai di banyak halaman.

## Hasil
<img width="1917" height="1198" alt="image" src="https://github.com/user-attachments/assets/54b6a16f-99fc-4511-b0c2-a8ac345ce249" />
