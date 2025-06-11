---
title: Fractional Knapsack Problem
date: 2025-06-11 11:00:00 +0800
categories: [Algoritma, Problem Solving]
tags: [greedy, knapsack, algoritma, coding]
math: true
---

## 🎒 Apa itu Fractional Knapsack?

**Fractional Knapsack Problem** adalah varian dari _knapsack problem_ di mana kita boleh mengambil **sebagian** dari suatu item. Berbeda dengan **0/1 Knapsack** (yang hanya memperbolehkan seluruh item atau tidak sama sekali), versi ini lebih fleksibel dan ideal untuk diselesaikan dengan **greedy algorithm**.

## 📦 Problem Statement

Diberikan:
- `n` buah item, masing-masing dengan berat `weight[i]` dan nilai `value[i]`
- Kapasitas tas `W`

Tujuan:
- Maksimalkan total nilai yang bisa dimasukkan ke dalam tas, dengan **boleh mengambil sebagian item** jika perlu.

## ⚙️ Langkah Penyelesaian (Greedy Approach)

1. Hitung rasio nilai per berat:  
   \( \text{value\_per\_weight}[i] = \frac{value[i]}{weight[i]} \)
2. Urutkan item berdasarkan rasio tersebut secara **menurun**.
3. Masukkan item satu per satu ke dalam tas:
   - Jika muat sepenuhnya, ambil seluruh item.
   - Jika tidak muat, ambil sebagian sesuai kapasitas sisa.

## 📐 Contoh Kasus

```text
Input:
Items = 3
Values = [60, 100, 120]
Weights = [10, 20, 30]
Capacity = 50

Langkah:
- value/weight = [6, 5, 4]
- Ambil item 1 (60, 10kg)
- Ambil item 2 (100, 20kg)
- Ambil 20kg dari item 3 (2/3 dari 120 = 80)

Output:
Total Value = 240
