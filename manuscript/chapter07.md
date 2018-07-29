# Menyimpan data dalam array

Pada bab ini Anda akan diperkenalkan tentang [arrays]( https://en.wikipedia.org/wiki/Array_data_type ), sebuah tipe data dalam variable yang digunakan oleh program komputer untuk menyimpan data.

## TL;DR

* Sebuah array merepresentasikan daftar element. Sebuah array JavaScript adalah object yang memiliki property yang spesial, seperti `length` untuk mengakses ukurannya (jumlah elemen).

* Anda dapat mengandaikan array adalah sebuah kardus, di dalam kardus berisi nilai yang spesifik dan berasosiasi dengan angka yang disebut dengan **index**. Elemen pertama dari sebuah array berupa index dengan angka 0 - bukan 1.

* Anda dapat mengakses beberapa elemen melalui index dengan tanda **kurung kotak** `[]`.

* Untuk melakukan perulangan pada array (mencari elemen per elemen), Anda dapat menggunakan perulangan `for`, method `forEach()` atau perulangan `for-of`.

```js
for (let i = 0; i < myArray.length; i++) {
  // Gunakan myArray[i] untuk mengakses setiap elemen dari array satu per satu
}

myArray.forEach(myElement => {
  // Gunakan myElement untuk mengakses elemen dari array satu per satu
});

for (const myElement of myArray) {
  // Gunakan myElement untuk mengakses elemen dari array satu per satu
}
```

* Method `push()` untuk menambahkan sebuah elemen pada akhir sebuah array. Method `unshift()` menambahkan elemen di awal sebuah array.

* Method `pop()` dan `splice()` digunakan untuk menghapus elemen dari array.

## Pengenalan array

Bayangkan Anda ingin membuat sebuah daftar yang berisi semua film yang telah anda lihat di tahun ini.

Satu solusi akan digunakan untuk menambahkan beberapa variabel:

```js
const movie1 = "The Wolf of Wall Street";
const movie2 = "Zootopia";
const movie3 = "Babysitting";
// ...
```

Jika Anda seorang penggemar film, Anda mungkin akan menemukan diri anda menggunakan banyak variable di program Anda. Bagian terburuk adalah variabel-variabel ini benar-benar independen satu sama lain.

Kemungkinan lain adalah menambahkan daftar film ke dalam object.

```js
const movies = {
  movie1: "The Wolf of Wall Street",
  movie2: "Zootopia",
  movie3: "Babysitting",
  // ...
};
```

Kali ini, data terpusat dalam sebuah object `movies`. Nama dari property nya (`movie1`, `movie2`, `movie3`...), bagaimanapun, tidak perlu dan berulang - ulang.

Anda membutuhkan sebuah solusi untuk menyimpan banyak hal bersamaan tanpa memberi nama secara manual!

Untungnya, ada sebuah solusi: menggunakan sebuah array. Sebuah **array** adalah tipe data untuk menyimpan daftar elemen.

## Manipulasi array di JavaScript

Di JavaScript, sebuah array adalah object yang memiliki property yang khusus.

### Membuat array

Berikut adalah cara membuat daftar film kita dalam bentuk array.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
```

Sebuah array dibuat menggunakan sepasang kurung siku `[]`. Semua dengan tanda kurung siku membuat array.

Anda dapat menyimpan beberapa tipe yang berbeda dengan sebuah array, termasuk string, number, boolean bahkan object.

```js
const elements = ["Hello", 7, { message: "Hi mom" }, true];
```

> Sejak array mungkin memiliki banyak elemen, sebaiknya berikan nama array yang jamak (contoh, `movies`).

### Memperoleh ukuruan array

Jumlah elemen yang disimpan di dalam array disebut dengan **size**. Berikut adalah cara mengaksesnya.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
console.log(movies.length); // 3
```

Anda mengakses ukuran pada sebuah array melalui property `length`, menggunakan notasi dot.

Tentunya, property `length` mengembalikan nilai 0 jika array tersebut kosong.

```js
const emptyArray = []; // Membuat array kosong
console.log(emptyArray.length); // 0
```

### Mengakses sebuah elemen pada array

Setiap hal pada array diidentifikasikan berdasarkan angka yang disebut dengan **index** - sebuah pointer integer yang mengidentifikasi sebuah elemen pada array. 
The index of the last array element would be the array's size minus 1.
Anda dapat mengandaikan array adalah sebuah kardus, di dalam kardus berisi nilai yang spesifik dan berasosiasi dengan index. Trik: Elemen pertama dari sebuah array berupa index dengan angka 0 - bukan 1, elemen kedua adalah index dengan angka 1, dan seterusnya.
Index dari elemen terakhir array akan menjadi ukuran array dikurangi 1.

![Representasi array movies](images/chapter07-01.png)

Anda dapat mengakses sebuah elemen tertentu dengan memberikan index nya menggunakan **kurung siku** `[]`:

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
console.log(movies[0]); // "The Wolf of Wall Street"
console.log(movies[1]); // "Zootopia"
console.log(movies[2]); // "Babysitting"
```

Menggunakan index yang invalid untuk mengakses elemen array JavaScript akan mengembalikan nilai `undefined`.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
console.log(movies[3]); // undefined: elemen terakhir adalah pada index 2
```

## Perulangan melalui array

Terdapat beberapa cara untuk mencari elemen sebuah array.

Pertama adalah menggunakan perulangan for seperti yang disampaikan sebelumnya.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
for (let i = 0; i < movies.length; i++) {
  console.log(movies[i]);
}
```

Perulangan `for` menjalankan setiap elemen pada array dimulai dari index 0 sampai dengan ukuran array dikurangi 1, yang mana itu adalah elemen terakhir.

Cara lain adalah menggunakan method `forEach()` method pada array. Ia mengambil sebuah parameter **function** yang akan diterapkan di setiap elemen array.

```js
myArray.forEach(myElement => {
  // Gunakan myElement untuk mengakses elemen dari array satu per satu
});
```

Berikut adalah contoh sebelumnya, ditulis ulang dengan method ini dan sebuah fungsi fat arrow `=>`.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
movies.forEach(movie => {
  console.log(movie);
});
```

Selama eksekusi, setiap elemen array dilewati sebagai parameter (diberi nama `movie` pada contoh ini) pada fungsi yang berasosiasi pada `forEach()`.

Terakhir, Anda dapat penggunakan perulangan `for-of` loop, sebuah jenis khusus untuk perulangan object [iterable objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols#iterable) seperti array. Ini adalah sintaksnya.

```js
for (const myElement of myArray) {
  // Gunakan myElement untuk mengakses elemen dari array satu per satu
}
```

Perhatikan contoh yang telah ditulis ulang dengan perulangan `for-of`.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
for (const movie of movies) {
  console.log(movie);
}
```

## Mengubah isi sebuah array

### Menambahkan elemen pada array

Jangan berbohong pada saya: Anda baru saha menonton Ghostbusters namun di lain waktu. Mari tambahkan ke dalam daftar movies. Berikut cara Anda melakukannya.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
movies.push("Ghostbusters");
console.log(movies[3]); // "Ghostbusters"
```

Anda menambahkan sebuah hal baru ke dalam array menggunakan method `push()`. Elemen baru yang akan ditambahkan dilewatkan sebagai parameter ke method. Hal tersebut ditambahkan ke dalam akhir array.

Untuk menambahkan elemen di awal array, gunakan method `unshift()` daripada `push()`.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
movies.unshift("Pacific Rim");
console.log(movies[0]); // "Pacific Rim"
```

### Menghapus elemen pada array

Anda dapat menghapus elemen akhir pada sebuah array menggunakan method `pop()`.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
movies.pop(); // Menghapus elemen terakhir array
console.log(movies.length); // 2
console.log(movies[2]); // undefined
```

Sebagai alternatif, Anda dapat menggunakan method `splice()` dengan dua parameter: pertama adalah index darimana mulai menghapus, kedua adalah jumlah elemen yang dihapus.

```js
const movies = ["The Wolf of Wall Street", "Zootopia", "Babysitting"];
movies.splice(0, 1); // Menghapus 1 elemen dimulai pada index 0
console.log(movies.length); // 2
console.log(movies[0]); // "Zootopia"
console.log(movies[1]); // "Babysitting"
```

## Waktunya Koding!

Buatlah semua program ini dengan mode umum: Semua keluaran program sebaiknya mencerminkan pembaharuan apa pun dalam array.

### Musketeers

Buatlah sebuah program yang:

* Membuat array bernama `musketeers` berisi nilai "Athos", "Porthos" and "Aramis".
* Menampilkan setiap elemen array menggunakan perulangan `for`.
* Menambahkan nilai "D'Artagnan" ke dalam array.
* Menampilkan setiap elemen array menggunakan method `forEach()`.
* Menghapus nilai Aramis.
* Menampilkan setiap elemen array menggunakan perulangan `for-of`.

### Menjumlahkan nilai

Tulis sebuah program berdasarkan array di bawah, kemudian tampilkan total jumlah dari nilai tersebut (hasilnya adalah 42).

```js
const values = [3, 11, 7, 2, 9, 10];
```

### Array maksimum

Tulis sebuah program berdasarkan array di bawah, kemudian tampilkan nilai maksimum dari array tersebut.

```js
const values = [3, 11, 7, 2, 9, 10];
```

### Daftar kata

Tulislah sebuah program yang meminta user untuk menginputkan sebuah kata sampai user mengetik kata "stop". Kemudian program tersebut menampilkan setiap kata kecuali kata "stop".