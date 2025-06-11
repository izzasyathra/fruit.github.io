---
title: Dijkstra's Algorithm (Pencarian Jalur Terpendek)
date: 2025-06-11 14:30:00 +0800
categories: [Algoritma, Graph]
tags: [dijkstra, shortest path, graph, algoritma]
math: false
---

## 🚀 Apa itu Dijkstra's Algorithm?

**Dijkstra’s Algorithm** adalah algoritma pencarian jalur terpendek dari satu node sumber ke semua node lain dalam graf **berarah atau tak berarah**, **berbobot non-negatif**.

---

## 📚 Konsep Dasar

Dijkstra memanfaatkan:
- **Priority Queue / Min-Heap** untuk memilih node dengan jarak terkecil
- **Array / Map jarak** untuk menyimpan jarak minimum ke setiap node

---

## 💡 Cara Kerja

1. Inisialisasi semua jarak sebagai ∞, kecuali node sumber (0)
2. Masukkan sumber ke min-heap
3. Selama heap tidak kosong:
   - Ambil node dengan jarak terkecil
   - Update jarak tetangganya jika lebih kecil
   - Tambahkan tetangga ke heap jika ada update

---

## 💻 Contoh Kode Python (Menggunakan `heapq`)

```python
import heapq

def dijkstra(graph, start):
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    pq = [(0, start)]

    while pq:
        current_dist, current_node = heapq.heappop(pq)

        if current_dist > distances[current_node]:
            continue

        for neighbor, weight in graph[current_node]:
            distance = current_dist + weight
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(pq, (distance, neighbor))

    return distances

# Contoh graf berbobot
graph = {
    'A': [('B', 1), ('C', 4)],
    'B': [('C', 2), ('D', 5)],
    'C': [('D', 1)],
    'D': []
}

print("Jarak terpendek dari A:")
print(dijkstra(graph, 'A'))
# Output: {'A': 0, 'B': 1, 'C': 3, 'D': 4}
