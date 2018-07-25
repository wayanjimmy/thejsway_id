# Kondisi

# Rangkuman

* Kata kunci `if` mendefinisikan kondisional. Kode block yang ada didalam `if` hanya akan dijalankan jika kondisi memenuhi (mengembalikan nilai `true`).

```js
if (kondisi) {
    // Kode yang dijalankan jika kondisi mengembalikan nilai true
}
```

* Kode block didalam `if` di diapit dengan tanda kurung kurawal (`{...}`). Untuk mempermudah pembacaan kode block ditambahkan indentasi.

* Operator pembanding seperti `===`, `!==`, `<=`, `>=`, `>` dan `<` didalam kondisi semua operator tersebut mengembalikan nilai boolean.
 
* `if` dapat berisikan (opsional) statement `else` untuk menambahkan kode yang perlu dieksekusi jika kondisi mengembalikan nilai `false`

```js
if (kondisi) {
    // Kode yang dijalankan jika kondisi mengembalikan nilai true
} else {
    // Kode yang dijalankan jika kondisi mengembalikan nilai false
}
```

### Apa itu Kondisi ?

Bayangkan jika kita akan membuat program yang menerima sebuah input angka kemudian menampilkan pesan jika angka positif.

```
Masukan sebuah angka
Jika angka positif
    Tampilkan sebuah pesan
```

### Statement `if` 

Berikut adalah program diatas yang ditulis dalam Javascript.
```js
const number = Number(prompt("Masukan sebuah angka:"));
if (number > 0) {
    console.log(`${number} adalah positif`);
}
```

### Kondisi

Sebuah kondisi adalah ekspresi yang mengevaluasi sebuah nilai apakah bernilai `true` atau `false`, nilai ini disebuat Boolean. Jika kondisi mengembalikan nilai `true` maka kondisi tersebut terpenuhi.

Sebelumnya sudah kita pelajari tipedata String dan Number, Boolean ada tipedata yang lainnya.

```js
if (true) {
  // Kondisi ini selalu true
  // Kode block didalamnya akan selalu dieksekusi
}
if (false) {
  // Kondisi ini selalu false
  // Kode block didalamnya tidak akan pernah dieksekusi
}
```

Ekspresi yang mengembalikan nilai Boolean dapat dilakukan dengan operator berikut.

|Operator|Kegunaan|
|---------|----|
|`===`|Nilainya sama|
|`!==`|Nilainya tidak sama|
|`<`|Kurang dari|
|`<=`|Kurang dari sama dengan|
|`>`|Lebih dari|
|`>=`|Lebih dari sama dengan|

Sekarang coba untuk mengubah kode diatas menjadi seperti ini.
```js
const number = Number(prompt("Masukan sebuah angka:"));
if (number >= 0) {
    console.log(`${number} adalah positif atau nol`);
}
```

## Kondisi alternatif

### Statement `else`

Tambahkan kode diatas dengan statement `else`

```js
const number = Number(prompt("Masukan sebuah angka:"));
if (number > 0) {
    console.log(`${number} adalah positif atau nol`);
} else {
    console.log(`${number} adalah negatif atau nol`);
}
```