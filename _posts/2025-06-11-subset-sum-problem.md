---
title: Subset Sum Problem
date: 2025-06-11 12:00:00 +0800
categories: [Algoritma, Problem Solving]
tags: [subset sum, dynamic programming, algoritma, coding]
math: false
---

## 📌 Apa itu Subset Sum Problem?

**Subset Sum Problem** adalah masalah klasik dalam teori algoritma, di mana kita diberikan sebuah set angka dan sebuah nilai target, dan tugas kita adalah menentukan apakah ada subset dari angka-angka tersebut yang jumlahnya sama dengan nilai target.

Contoh:
- Set: `{3, 34, 4, 12, 5, 2}`
- Target: `9`
- Apakah ada subset yang jumlahnya 9?  
  Jawaban: **Ya**, subset `{4, 5}` memiliki jumlah 9.

## ⚙️ Pendekatan Penyelesaian

### 1. **Brute Force Approach**:
   - Coba semua kemungkinan subset dari set yang diberikan dan periksa apakah jumlahnya sama dengan target. Ini memiliki kompleksitas waktu **O(2^n)**, yang tidak efisien.

### 2. **Dynamic Programming Approach**:
   - Gunakan tabel 2D untuk menyimpan apakah subset dengan jumlah tertentu dapat dibentuk dengan menggunakan elemen-elemen yang ada. Pendekatan ini memiliki kompleksitas waktu **O(n * target)**, lebih efisien dibanding brute force.

## 💻 Contoh Kode (Python) - Dynamic Programming

```python
def is_subset_sum(arr, target):
    n = len(arr)
    dp = [[False for _ in range(target + 1)] for _ in range(n + 1)]

    # Jika target 0, jawabannya selalu True (subset kosong)
    for i in range(n + 1):
        dp[i][0] = True

    # Isi tabel dp
    for i in range(1, n + 1):
        for j in range(1, target + 1):
            if arr[i-1] <= j:
                dp[i][j] = dp[i-1][j] or dp[i-1][j-arr[i-1]]
            else:
                dp[i][j] = dp[i-1][j]

    return dp[n][target]

# Contoh penggunaan
arr = [3, 34, 4, 12, 5, 2]
target = 9
print(f"Apakah ada subset dengan jumlah {target}? {is_subset_sum(arr, target)}")
# Output: Apakah ada subset dengan jumlah 9? True
