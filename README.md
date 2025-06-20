# 🔁 Undoable Dynamic Network System

This project is a Python-based mini project developed for an Algorithms and Data Structures course. It introduces a **modular and undo-capable system** for managing a network of interconnected elements using three core classes:

- `ArrayListWithUndo`: A list structure extended with undo capability.
- `NetworkWithUndo`: A disjoint-set (union-find) structure with undo support.
- `Gadget`: A user-level wrapper providing named elements, dynamic subnet management, and clean undo features.

---

## ✨ Features

- Add/remove elements with full undo support.
- Efficient **union-find with path compression**.
- Connect/disconnect elements with undoable merge operations.
- Clean/remove all operations related to a node.
- Identify and return **connected subnetworks**.
- Stack-based tracking for all reversible operations.

---

## 🧠 Class Overview

### 🔹 `ArrayListWithUndo`

Enhances a standard dynamic array with undo tracking:
- `append(v)`: Adds a value and stores a removal instruction.
- `insert(i, v)`: Inserts at index and stores removal.
- `remove(i)`: Removes value and stores re-insertion.
- `undo()`: Reverses the latest operation from the stack.

### 🔹 `NetworkWithUndo`

Implements a union-find network:
- `add()`: Adds a new cluster.
- `root(i)`: Finds root of node `i` with path compression and undo support.
- `merge(i, j)`: Merges clusters with size tracking.
- `undo()`: Reverses last merge/add/set batch of operations.

### 🔹 `Gadget`

Builds a named node-level abstraction over the network:
- `add(name)`: Adds a node with a unique name.
- `connect(name1, name2)`: Merges networks.
- `clean(name)`: Reverts all operations since the node was added.
- `subnets()`: Returns all connected subgraphs.
- `undo(n)`: Reverses the last `n` named operations.

---

## 🧪 Sample Usage

```python
g = Gadget()
g.add("A")
g.add("B")
g.connect("A", "B")
print(g.subnets())  # [['A', 'B']]
g.undo(1)
print(g.subnets())  # [['A'], ['B']]
