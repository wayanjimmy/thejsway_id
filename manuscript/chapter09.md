# Mengenali Pemrograman Berorientasi Obyek

Beberapa bab sebelumnya Anda telah belajar bagaimana membuat object di Javascript. Sekarang saatnya mengenalinya dengan lebih baik.

## Rangkuman 

* **Pemrograman Berorientasi Objek** atau OOP adalah [paradigma pemrograman](https://en.wikipedia.org/wiki/Programming_paradigm) yang menggunakan Objek yang berisikan **data** dan **kelakuan** untuk membuat program.

* **Class** adalah sebuah abstraksi konsep atau ide dalam pemrograman berorientasi objek. Konsep ini menawarkan syntax yang nyaman dalam merepresentasikan objek.

* Dalam Javascript class didefinisikan dengan kata kunci `class`. Class hanya dapat berisikan **method**. Method `constructor()` yang dipanggil ketika object dibuat, digunakan untuk melakukan inisialisasi objek, biasanya digunakan untuk mengisikan properi pada objek. Didalam method, kata kunci `this` merepresentasikan **object dimana method itu dipanggil**.

```js
class SebuahClass {
  constructor(param1, param2, ...) {
    this.property1 = param1;
    this.property2 = param2;
  }
  method(/* ... */) {
    // ...
  }
  method2(/* ... */) {
    // ...
  }
  // ...
}
```
