# Perulangan

## Rangkuman

* **Perulangan** digunakan untuk mengulang statement. Setiap pengulangan disebut **iterasi**. Block kode yang diasosiasikan dengan perulangan disebut **body**.

* Perulangan dengan `while` mengulang statement selama kondisi terpenuhi. Perulangan `for` memberikan kendali untuk mengatur apa yang terjadi sesaat sebelum dan setelah iterasi terjadi.

```js
// Perulangan while
while (kondisi) {
    // Kode yang dieksekusi selama kondisi true
}

for (inisialisasi; kondisi; ekspresi akhir) {
    // Kode yang dieksekusi selama kondisi true
}
```

* Variabel yang mengatur perulangan disebut dengan **counter** sering dinamankan dengan `i`.

## Pengenalan

Jika Anda menulis program yang menampilkan angka 1 sampai 5, Anda dapat menulis seperti ini.

```js
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);
```

akan melelahkan dan rumit untuk menulis program yang menampilkan angka antara 1 dan 1000, misalnya. Bagaimana Anda bisa membuat hal yang sama dengan lebih mudah?

JavaScript memungkinkan Anda menulis kode di dalam **perulangan** yang berulang kali dijalankan hingga berhenti. Setiap kali kode berjalan, itu disebut **iterasi**.

## Perulangan `while`

### Contoh

```js
let number = 1;
while (number <= 5) {
  console.log(number);
  number++;
}
```

![Hasil eksekusi](images/chapter04-02.png)

## Perulangan `for`

### Contoh

```js
let number;
for (number = 1; number <= 5; number++) {
  console.log(number);
}
```

## Kesalahan umum

Risiko utama menggunakan perulangan `while` loops adalah menghasilkan **infinite loops** (perulangan tiada akhir), yang berarti kondisi selalu benar, dan kode berjalan selamanya.

```js
let number = 1;
while (number <= 5) {
  console.log(number);
  // Variable number tidak berubah nilainya menyebabkan kondisi selalu true dan tidak berubah
}
```

## Waktunya Koding!

### Validasi input

Tulis program yang akan terus meminta input, sampai input yang dimasukan adalah angka yang kurang dari sama dengan 100. Jika sudah coba ubah kondisi menjadi angka diantara 50 sampai 100.

### Tabel perkalian

Tulis program yang meminta input angka dan menampilkan tabel perkalian angka tersebut. Jika sudah buat program Anda hanya menerima input angka antara 2 dan 9.

### FizzBuzz

Tulis program yang menampilkan angka antara 1 sampai 100 dengan pengecualian.

* Menampilkan `"Fizz"` jika angka habis dibagi 3
* Menampilkan `"Buzz"` jika angka habis dibagi 5 dan tidak habis jika dibagi 3

Jika sudah coba tambahkan kondisi menampilkan `"FizzBuzz"` jika angka habis dibagi 3 dan 5.
