---
title: Depth First Search (DFS)
date: 2025-06-11 13:30:00 +0800
categories: [Algoritma, Graph]
tags: [dfs, graph traversal, algoritma, rekursif, pencarian]
math: false
---

## 🧠 Apa itu Depth First Search (DFS)?

**Depth First Search (DFS)** adalah algoritma penelusuran graf atau pohon yang menjelajah **sedalam mungkin** pada satu cabang sebelum backtrack dan pindah ke cabang lain.

DFS cocok digunakan saat:
- Ingin mencari semua kemungkinan jalur
- Mendeteksi siklus dalam graf
- Menelusuri komponen terhubung

---

## ⚙️ Cara Kerja

DFS menjelajah dari simpul awal, lalu:
1. Tandai node sebagai dikunjungi
2. Telusuri salah satu tetangga yang belum dikunjungi
3. Ulangi proses hingga semua node dikunjungi

DFS bisa diimplementasikan:
- Secara **rekursif**
- Dengan **stack**

---

## 💻 Contoh Kode Python (DFS Rekursif)

```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()

    visited.add(node)
    print(node, end=' ')

    for neighbor in graph[node]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)

# Contoh graf
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}

print("Hasil DFS dari A:")
dfs(graph, 'A')
# Output: A B D E F C
