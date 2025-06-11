---
title: Kahn's Algorithm (Topological Sort)
date: 2025-06-11 14:00:00 +0800
categories: [Algoritma, Graph]
tags: [topological sort, kahn, graph, bfs, algoritma]
math: false
---

## 🧠 Apa itu Kahn's Algorithm?

**Kahn’s Algorithm** adalah salah satu metode untuk melakukan **Topological Sorting** pada graf berarah (**DAG - Directed Acyclic Graph**).

Topological Sort menyusun simpul graf sedemikian rupa sehingga **untuk setiap edge u → v, simpul u muncul sebelum simpul v** dalam urutan.

---

## ⚙️ Inti Ide Kahn's Algorithm

Kahn’s Algorithm menggunakan pendekatan **Breadth-First Search (BFS)** dengan konsep **indegree**:

1. Hitung indegree semua simpul (jumlah panah masuk).
2. Tambahkan simpul dengan indegree = 0 ke dalam queue.
3. Ambil simpul dari queue, tambahkan ke hasil urutan.
4. Kurangi indegree semua tetangganya.
5. Jika tetangga jadi indegree = 0, masukkan ke queue.
6. Ulangi sampai queue kosong.

Jika semua node bisa diproses → DAG valid.  
Jika tidak → Ada siklus (bukan DAG).

---

## 💻 Contoh Kode Python

```python
from collections import deque, defaultdict

def kahn_topological_sort(graph):
    indegree = defaultdict(int)
    for u in graph:
        for v in graph[u]:
            indegree[v] += 1

    queue = deque()
    for node in graph:
        if indegree[node] == 0:
            queue.append(node)

    topo_order = []

    while queue:
        u = queue.popleft()
        topo_order.append(u)

        for v in graph[u]:
            indegree[v] -= 1
            if indegree[v] == 0:
                queue.append(v)

    if len(topo_order) == len(graph):
        return topo_order
    else:
        return "Graph memiliki siklus (bukan DAG)"

# Contoh graf DAG
graph = {
    'A': ['C'],
    'B': ['C', 'D'],
    'C': ['E'],
    'D': ['F'],
    'E': ['F'],
    'F': []
}

print("Topological Sort (Kahn's Algorithm):")
print(kahn_topological_sort(graph))
# Output bisa: ['A', 'B', 'C', 'D', 'E', 'F]()

