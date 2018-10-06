# Mengenali pemrograman fungsional

Pemrograman berorientasi obyek, meskipun cukup populer, bukan satu-satunya cara untuk membuat untuk membuat program. Bab ini akan memperkenalkan paradigma penting yang lain; pemrograman fungsional



## TL;DR

- **Pemrograman fungsional** (*functional programming*) adalah tentang menulis program dengan mengkombinasikan / menggabungkan fungsi-fungsi yang mengekpresikan apa yang seharusnyadilakukan oleh program, daripada bagaimana melakukannya (yang merupakan cara penting).
- **Keadaan suatu** program adalah nilai dari **variabel globalnya** pada waktu tertentu. Tujuan
   dari pemrograman fungsional adalah untuk meminimalkan mutasi keadaan (perubahan) yang membuat kode lebih sulit untuk dipahami. Beberapa solusi yang mungkin mendeklarasikan variabel dengan `const` daripada `let`, membagi kode menjadi fungsi, dan mendukung variabel lokal di
   atas variabel global.
- **Fungsi murni** (*pure function*) hanya bergantung pada inputnya untuk menghitung outputnya dan **tidak memiliki efek samping**. Fungsi murni (*pure function*) lebih mudah dipahami, digabungkan bersama, dan debug. Pemrograman fungsional mendukung penggunaan fungsi murni jika memungkinkan.
- Metode `map()`, `filter()` dan `reduce()` dapat mengganti loop untuk array dan membiarkan program dengan array secara fungsional.
- Fungsi JavaScript dapat dibagikan seperti halnya nilai lainnya: mereka disebut dengan **first-class citizens**, yang memungkinkan pemrograman fungsional. Fungsi yang beroperasi pada fungsi lain (mengambilnya sebagai parameter atau mengembalikannya) disebut **higher-order function**.
- JavaScript adalah bahasa **multi-paradigma**: menulis program menggunakan 
  gaya pemrograman imperatif, berorientasi objek atau fungsional.



## Konteks: daftar film

Pada bab ini, di mulai dengan contoh program dan memperbaikinya sedikit demi sedikit, tanpa menambahkan fungsi baru apa pun. Tugas pemrograman penting ini disebut refactoring.

Program awal ini adalah tentang film Batman terbaru. Data tersebut datang dalam bentuk array objek, engan masing-masing objek menggambarkan film.

```js
const daftarFilm = [
  {
    judul: "Batman",
    tahun: 1989,
    direktur: "Tim Burton",
    peringkatImb: 7.6
  },
  {
    judul: "Batman Returns",
    tahun: 1992,
    direktur: "Tim Burton",
    peringkatImb: 7.0
  },
  {
    judul: "Batman Forever",
    tahun: 1995,
    direktur: "Joel Schumacher",
    peringkatImb: 5.4
  },
  {
    judul: "Batman & Robin",
    tahun: 1997,
    direktur: "Joel Schumacher",
    peringkatImb: 3.7
  },
  {
    judul: "Batman Begins",
    tahun: 2005,
    direktur: "Christopher Nolan",
    peringkatImb: 8.3
  },
  {
    judul: "The Dark Knight",
    tahun: 2008,
    direktur: "Christopher Nolan",
    peringkatImb: 9.0
  },
  {
    judul: "The Dark Knight Rises",
    tahun: 2012,
    direktur: "Christopher Nolan",
    peringkatImb: 8.5
  }
];
```

Dan inilah sisa program yang digunakannya, itu seharusnya sudah cukup jelas.

```javascript
// Dapatkan judul film
const judulJudul = [];
for (const film of daftarFilm) {
  judulJudul.push(film.judul);
}
console.log(judulJudul);

// Hitung film berdasarkan Christopher Nolan
const daftarFilmNolan = [];
for (const film of daftarFilm) {
  if (film.direktur === "Christopher Nolan") {
    daftarFilmNolan.push(film);
  }
}
console.log(daftarFilmNolan.length);

// Dapaktkan judul-judul film dengan peringkat IMDB lebih atau sama dengan 7.5
const judulJudulTerbaik = [];
for (const film of daftarFilm) {
  if (film.peringkatImb >= 7.5) {
    judulJudulTerbaik.push(film.judul);
  }
}
console.log(judulJudulTerbaik);

// Hitung rata-rata peringkat film yang di buat oleh Christopher Nolan
let peringkat = 0;
let peringkatRataRata = 0;
for (const film of daftarFilmNolan) {
  peringkat += film.peringkatImb;
}
peringkatRataRata = peringkat / daftarFilmNolan.length;
console.log(peringkatRataRata);
```

![](/home/hello/Projects/Contributes/thejsway_id/manuscript/images/chapter10-01.png)



## Keadaan program (Program state)

Program sebelumnya adalah contoh dari apa yang disebut **pemrograman imperatif**. Dalam paradigma ini, programmer memberi perintah kepada komputer melalui serangkaian pernyataan yang mengubah status program. Pemrograman imperatif berfokus pada menggambarkan bagaimana suatu program beroperasi.

Konsep keadaan (*state*) adalah yang penting. **Keadaan** (*state*) suatu program adalah nilai dari v**ariabel globalnya** (variabel dapat diakses di mana saja dalam kode) pada waktu tertentu. Dalam contoh ini, nilai-nilai `daftarFilm`, `judul`, `daftarFilmNolan`, `judulJudulTerbaik`, `peringkat` dan `peringkatRataRata` bentuk status program. Setiap penugasan ke salah satu variabel ini adalah perubahan status, sering isebut **mutation**.

Dalam pemrograman imperatif, suatu *state* dapat dimodifikasi di mana saja dalam kode sumber. Ini nyaman, tetapi juga dapat menyebabkan bug jahat dan sakit kepala. Sebagai program yang tumbuh dalam ukuran dan kompleksitas, menjadi lebih mudah bagi programmer untuk bermutasi bagian dari *state* oleh kesalahan dan lebih sulit untuk memantau modifikasi *state*.



## Membatasi *mutation* dengan variabel `const`

Untuk mengurangi risiko *state mutation* disengaja, langkah pertama adalah 
memilih `const` daripada `let` kapanpun berlaku untuk deklarasi variabel. Variabel yang dideklarasikan dengan kata kunci `const` tidak dapat ditugasi lebih lanjut. Array dan *object content* masih bisa dimutasi. Periksa kode berikut untuk detailnya.

```javascript
const n = 10;
const buah = "Pisang";
const obj = {
  propSaya: 2
};
const binatangBinatang = ["Gajah", "Anjing"];

obj.propSaya = 3; // Mutation properti akan baik-baik saja walaupun untuk objek const

obj.propSayaYangLain = "abc"; // Menambah sebuah properti baru akan baik-baik saja walaupun untuk objek const
binatangBinatang.push("Monyet"); // Memperbarui konten akan baik-baik saja walaupun untuk objek const

n++; // Ilegal
buah = "orange"; // Ilegal
obj = {}; // Ilegal
binatangBinatang = ["Beruang"]; // Ilegal
```



## Membagi program menjadi beberapa fungsi

Solusi lain adalah membagi kode ke dalam sub rutin yang disebut ***procedures*** atau ***functions***. Hal ini disebut ***procedural programming*** dan memiliki manfaat mengubah 
beberapa variabel menjadi ***local variables***, yang hanya terlihat dalam kode
 sub rutin.

Mari mencoba memperkenalkan beberapa fungsi dalam kode ini

```javascript
// Dapatkan judul film
const judulJudul = () => {
  const judulJudul = [];
  for (const film of daftarFilm) {
    judulJudul.push(film.judul);
  }
  return judulJudul;
};

const daftarFilmNolan = [];

// Dapatkan Film dari Christopher Nolan
const filmFilmNolan = () => {
  for (const film of daftarFilm) {
    if (film.direktur === "Christopher Nolan") {
      daftarFilmNolan.push(film);
    }
  }
};

// Dapaktkan judul-judul film dengan peringkat IMDB lebih atau sama dengan 7.5
const judulJudulTerbaik = () => {
  const judulJudulTerbaik = [];
  for (const film of daftarFilm) {
    if (film.peringkatImb >= 7.5) {
      judulJudulTerbaik.push(film.judul);
    }
  }
  return judulJudulTerbaik;
};

// Hitung rata-rata peringkat film yang di buat oleh Christopher Nolan
const peringkatRataRataNolan = () => {
  let peringkat = 0;
  for (const film of daftarFilmNolan) {
    peringkat += film.peringkatImb;
  }
  return peringkat / daftarFilmNolan.length;
};

console.log(judulJudul());
filmFilmNolan();
console.log(daftarFilmNolan.length);
console.log(judulJudulTerbaik());
console.log(peringkatRataRataNolan());
```

*State* dari program tersebut sekarang terbatas pada dua variabel: `daftarFilm` dan `daftarFilmNolan` (yang terakhir diperlukan dalam fungsi `filmFilmNolan()` dan `peringkatRataRataNolan ()`). Variabel lain sekarang lokal untuk fungsi yang digunakan, yang membatasi kemungkinan *state mutation* disengaja. Juga, versi program ini lebih mudah dipahami daripada versi sebelumnya. Fungsi dengan nama yang sesuai membantu menggambarkan perilaku suatu program. Komentar sekarang kurang diperlukan dari sebelumnya.



## Fungsi murni *(pure functions)*

Hanya memperkenalkan beberapa fungsi dalam suatu program tidak cukup untuk mengikuti paradigma pemrograman fungsional. Kapan pun memungkinkan, kita juga perlu menggunakan fungsi murni.

Fungsi murni ***pure functions*** adalah fungsi yang memiliki karakteristik sebagai berikut:

- Hasilnya hanya bergantung pada inputnya.
- Tidak mempunyai efek samping (*side effect*)

Efek samping (*side effect*) adalah perubahan dalam status program atau interaksi dengan dunia luar. Akses *database* atau pernyataan `console.log ()` adalah contoh efek samping.

Dengan data yang sama, fungsi murni akan selalu menghasilkan hasil yang sama. Dengan desain, fungsi murni adalah independen dari keadaan program dan tidak boleh mengaksesnya. Fungsi seperti itu harus menerima ***parameters*** untuk melakukan sesuatu yang bermanfaat. Satu-satunya cara untuk fungsi tanpa parameter menjadi murni adalah mengembalikan nilai konstan.

Fungsi-fungsi murni lebih mudah dipahami, digabungkan bersama, dan debug: tidak perlu melihat keluar dari tubuh fungsi untuk memikirkannya. Namun, sejumlah efek samping diperlukan dalam program apa pun, seperti menampilkan *output* kepada pengguna atau memperbarui *database*. Dalam pemrograman fungsional, nama *game* ini adalah untuk menciptakan efek samping itu hanya di beberapa bagian program yang dikhususkan dan diidentifikasi dengan jelas. Sisa dari kode harus ditulis sebagai fungsi murni.

Mari refactor kode contoh kami untuk memperkenalkan fungsi murni.

```javascript
// Dapatkan judul film
const judulJudul = filmFilm => {
  const judulJudul = [];
  for (const film of filmFilm) {
    judulJudul.push(film.judul);
  }
  return judulJudul;
};

// Dapatkan Film dari Christopher Nolan
const filmFilmNolan = filmFilm => {
  const filmFilmNolan = [];
  for (const film of filmFilm) {
    if (film.direktur === "Christopher Nolan") {
      filmFilmNolan.push(film);
    }
  }
  return filmFilmNolan;
};

// Dapaktkan judul-judul film dengan peringkat IMDB lebih atau sama dengan 7.5
const judulJudulTerbaik = filmFilm => {
  const judulJudulTerbaik = [];
  for (const film of filmFilm) {
    if (film.peringkatImb >= 7.5) {
      judulJudulTerbaik.push(film.judul);
    }
  }
  return judulJudulTerbaik;
};

// Hitung rata-rata peringkat film yang di buat oleh Christopher Nolan
const peringkatRataRata = filmFilm => {
  let peringkat = 0;
  for (const film of filmFilm) {
    peringkat += film.peringkatImb;
  }
  return peringkat / filmFilm.length;
};

console.log(judulJudul(daftarFilm));
const daftarFilmNolan = filmFilmNolan(daftarFilm);
console.log(daftarFilmNolan.length);
console.log(judulJudulTerbaik(daftarFilm));
console.log(peringkatRataRata(daftarFilmNolan));
```



## Operasi array *(Array operations)*

Pemrograman fungsional adalah tentang menulis program dengan menggabungkan fungsi-fungsi yang mengekspresikan *apa* yang seharusnya dilakukan oleh program, daripada *bagaimana* melakukannya. JavaScript menawarkan beberapa metode terkait array yang mendukung gaya pemrograman fungsional.

### Metode `map()`

Metode `map()` mengambil array sebagai parameter dan membuat array baru dengan hasil memanggil fungsi yang disediakan pada setiap elemen dalam array ini. Penggunaan `map()` yang khas adalah untuk mengganti loop untuk array.

```javascript
const numbers = [1, 5, 10, 15];
// membuat fungsi untuk setiap array akan di kali 2
const doubles = numbers.map(x => x * 2);

console.log(numbers); // [1, 5, 10, 15] (tidak ada perubahan)
console.log(doubles); // [2, 10, 20, 30]
```

Beginilah `judulJudul()` bisa ditulis ulang menggunakan `map()`. Lihatlah bagaimana kode fungsi sekarang lebih ringkas dan ekspresif.

```javascript
// Dapatkan judul film
const judulJudul = filmFilm => {
  /* Kode sebelumnya
  const judulJudul = [];
  for (const film of filmFilm) {
    judulJudul.push(film.judul);
  }
  return judulJudul;
  */

  // Return a new array containing only movie titles
  return filmFilm.map(film => film.judul);
};
```



### Metode `filter()`

Metode `filter()` menawarkan cara untuk menguji setiap elemen array terhadap fungsi yang disediakan. Hanya elemen yang lulus tes ini ditambahkan ke array yang dikembalikan.

```javascript
const numbers = [1, 5, 10, 15];
// Simpan ke dalam array jika number lebih dari atau sama dengan 10
const bigOnes = numbers.filter(x => x >= 10);

console.log(numbers); // [1, 5, 10, 15] (tidak ada perubahan)
console.log(bigOnes); // [10, 15]
```

Gunakan metode ini untuk fungsi `filmFilmNolan()`

```javascript
// Dapatkan Film dari Christopher Nolan
const filmFilmNolan = filmFilm => {
  /* Kode sebelumnya
  const filmFilmNolan = [];
  for (const film of filmFilm) {
    if (film.direktur === "Christopher Nolan") {
      filmFilmNolan.push(film);
    }
  }
  return filmFilmNolan;
  */

  // Return a new array containing only movies by Christopher Nolan
  return filmFilm.filter(film => film.direktur === "Christopher Nolan");
};
```

Metode `map()` dan `filter()` dapat digunakan bersama untuk mendapatkan efek yang kuat. mari gunakan pada `judulJudulTerbaik()`

```javascript
// Dapaktkan judul-judul film dengan peringkat IMDB lebih atau sama dengan 7.5
const judulJudulTerbaik = filmFilm => {
  /* Kode sebelumnya
  const judulJudulTerbaik = [];
  for (const film of filmFilm) {
    if (film.peringkatImb >= 7.5) {
      judulJudulTerbaik.push(film.judul);
    }
  }
  return judulJudulTerbaik;
  */
  
    return filmFilm.filter(film => film.peringkatImb >= 7.5).map(film => film.judul);
};
```



### Metode `reduce()`

Metode `reduce()` menerapkan fungsi yang disediakan ke setiap elemen array untuk menguranginya menjadi satu nilai. Metode ini biasanya digunakan untuk melakukan perhitungan pada suatu array.

```javascript
const numbers = [1, 5, 10, 15];
// Hitung hasil jumlah dari elemen array
const sum = numbers.reduce((acc, value) => acc + value, 0);

console.log(numbers); // [1, 5, 10, 15] (tidak ada perubahan)
console.log(sum);     // 31
```

