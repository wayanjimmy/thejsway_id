# Bermain dengan Variabel

## Rangkuman

* **Variabel** adalah media penyimpanan informasi. Setiap **variabel** memiliki nama, nilai dan tipedata. Dalam javascript tipedata tidak perlu dituliskan saat deklarasi variabel, karena Javascript adalah bahasa dengan tipe dinamis.

* **Variabel** di deklarasi dengan kata kunci `let` diikuti dengan nama variabel. Untuk mendeklarasi konstanta (variabel yang nilai awalnya tidak akan berubah) digunakan kata kunci `const`.

* Untuk memberi nilai variabel, digunakan tanda sama dengan `=`. Pada tipedata Number operator `+=` dan `++` dapat digunakan untuk menambah value variabel tersebut.

* **Scope** dari variabel adalah ruang lingkup dimana variabel tersebut dapat diakses. Variabel yang di deklarasi dengan `let` atau `const` adalah block scoped. Code block ditentukan dari kode yang diapit dengan tanda kurawal `{...}`

## Variabel

### Peran variabel

Program komputer menyimpan data menggunakan variabel. **Variabel** bisa dibayangkan sebagai sebuah kotak yang kita bisa isi benda didalamnya.

### Properti variabel

**Variabel** memiliki 3 properti utama.
* nama, Nama varibel dapat berisikan huruf kecil atau besar, angka (tidak diawal) dan karakter seperti (`$`) atau underscore (`_`)
* nilai, nilai atau informasi yang disimpan dalam variabel
* tipedata, menentukan peranan dan aksi yang dapat dilakukan ke variabel.

### Deklarasi Variabel

Sebelum Anda dapat menyimpan sebuah informasi di variabel, variabel harus dibuat dulu. Proses membuat variabel disebut dengan deklarasi variabel. Deklarasi variabel berarti komputer akan memesan memori sebagai tempat menampung variabel. Program kemudian dapat membaca dan menulis data ke memori melalui variabel.

```js
let a;
console.log(a);
```