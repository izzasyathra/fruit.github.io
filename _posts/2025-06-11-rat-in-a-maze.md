---
title: Rat in a Maze Problem
date: 2025-06-11 12:30:00 +0800
categories: [Algoritma, Backtracking]
tags: [backtracking, maze, algoritma, recursion, problem solving]
math: false
---

## 🐭 Apa itu Rat in a Maze Problem?

**Rat in a Maze** adalah masalah klasik pemrograman yang menyimulasikan seekor tikus yang harus menemukan jalan dari titik awal (pojok kiri atas) ke titik akhir (pojok kanan bawah) dalam sebuah **maze 2D**, di mana beberapa sel mungkin terhalang.

Tujuan:
- Temukan semua jalur dari start ke goal menggunakan **gerakan valid**, biasanya hanya ke **kanan (R)** dan **bawah (D)**, atau bisa juga ke 4 arah (U, D, L, R).

## 🧱 Representasi Maze

Maze direpresentasikan sebagai matriks 2D berisi:
- `1` → jalan yang bisa dilewati
- `0` → tembok (tidak bisa dilewati)

Contoh maze:

