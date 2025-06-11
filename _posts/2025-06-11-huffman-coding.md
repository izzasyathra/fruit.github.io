---
title: Huffman Coding
date: 2025-06-11 10:00:00 +0800
categories: [Algoritma, Kompresi Data]
tags: [huffman, encoding, algoritma, struktur data]
math: true
mermaid: true
---

## 🧠 Apa itu Huffman Coding?

**Huffman Coding** adalah algoritma kompresi data yang digunakan untuk mengurangi ukuran data tanpa kehilangan informasi (lossless compression). Teknik ini menggunakan _binary tree_ untuk mengkodekan karakter berdasarkan frekuensi kemunculannya.

## ⚙️ Cara Kerja

1. Hitung frekuensi tiap karakter dalam data.
2. Buat _priority queue_ dari karakter berdasarkan frekuensi.
3. Bangun pohon Huffman:
   - Gabungkan dua simpul dengan frekuensi terendah.
   - Ulangi sampai hanya ada satu simpul (root).
4. Tetapkan kode biner untuk tiap karakter:
   - Kiri = 0
   - Kanan = 1

## 📦 Contoh Sederhana

Misal: `"ABRACADABRA"`

| Karakter | Frekuensi |
|----------|-----------|
| A        | 5         |
| B        | 2         |
| R        | 2         |
| C        | 1         |
| D        | 1         |

Setelah dibangun pohonnya, tiap karakter mendapatkan kode biner yang lebih pendek jika frekuensinya lebih tinggi.

## ✅ Kelebihan

- Efisien untuk teks dengan karakter yang muncul tidak merata.
- Lossless (tidak ada data yang hilang).
- Digunakan dalam format file seperti ZIP, PNG, dll.

## ❗ Kekurangan

- Perlu pohon Huffman yang sama untuk encoding dan decoding.
- Tidak efisien jika distribusi karakter merata.

## 🧮 Ilustrasi Pohon Huffman (Mermaid)

```mermaid
graph TD
    Root --> A[0]
    Root --> Inner1[1]
    Inner1 --> B[10]
    Inner1 --> Inner2[11]
    Inner2 --> C[110]
    Inner2 --> D[111]
