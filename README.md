# 🎬 Degrees of Separation (CS50 AI Project 0)

This program determines the **degrees of separation** between two actors based on the movies they have starred in together.
It finds the **shortest connection** (if any) using a **Breadth-First Search (BFS)** algorithm.

---

## 📖 Overview

Given a dataset of actors, movies, and their relationships (from IMDb), the program builds a network graph where:

* **Nodes** represent people (actors).
* **Edges** represent shared movies between actors.

When you input two actor names, it calculates the **shortest path** between them — showing through which movies and co-stars they are connected.

For example:

```
Name: Tom Hanks
Name: Emma Watson
4 degrees of separation.
1: Tom Hanks and Gary Sinise starred in Forrest Gump
2: Gary Sinise and Kevin Bacon starred in Apollo 13
3: Kevin Bacon and Daniel Radcliffe starred in A Few Good Men
4: Daniel Radcliffe and Emma Watson starred in Harry Potter and the Sorcerer’s Stone
```

---

## ⚙️ How It Works

The program:

1. Loads data from CSV files (`people.csv`, `movies.csv`, `stars.csv`).
2. Constructs mappings of:

   * People → Movies they appeared in
   * Movies → People who starred in them
3. Uses **Breadth-First Search (BFS)** to find the shortest connection between two given actors.

---

## 📁 File Structure

```
degrees/
│
├── degrees.py         # Main program (this file)
├── util.py            # Helper classes: Node, StackFrontier, QueueFrontier
│
├── large/             # (Optional) Large dataset
│   ├── people.csv
│   ├── movies.csv
│   └── stars.csv
│
├── small/             # (Optional) Small dataset for testing
│   ├── people.csv
│   ├── movies.csv
│   └── stars.csv
│
└── README.md          # Documentation (this file)
```

---

## 🧠 Algorithm Details

### Search Algorithm

* **Breadth-First Search (BFS)** — ensures the shortest path between two actors.

### Node Structure

Each node represents a person:

* `state`: Person ID (the actor)
* `action`: Movie ID (the movie that connects them to their parent)
* `parent`: Previous node (previous actor in the chain)

### Frontier Structures

* `QueueFrontier`: Used for BFS (FIFO order)
* `StackFrontier`: Used for DFS (LIFO order, not used here but available)

### Search Logic

1. Start with the source actor.
2. Explore all neighboring actors (co-stars).
3. Continue level by level until the target actor is found.
4. Reconstruct the path from target back to source.

---

## ▶️ Usage

### 1. Clone or download the repository

```bash
git clone https://github.com/yourusername/degrees.git
cd degrees
```

### 2. Run the program

By default, it uses the **large** dataset:

```bash
python degrees.py
```

Or specify a dataset directory:

```bash
python degrees.py small
```

### 3. Input two names when prompted

```
Name: Tom Hanks
Name: Meg Ryan
```

The program will output the number of degrees of separation and the path of movies connecting them.

---

## 📊 Example Output

```
Loading data...
Data loaded.
Name: Tom Hanks
Name: Meg Ryan
1 degrees of separation.
1: Tom Hanks and Meg Ryan starred in Sleepless in Seattle
```

---

## 🧩 Dependencies

No external libraries are required — only Python’s built-in modules:

* `csv`
* `sys`
* `collections` (for deque)

Works with **Python 3.8+**

---

## 💡 Notes

* Handles **duplicate actor names** by asking you to choose a specific ID.
* Ignores missing or malformed CSV entries safely.
* Works efficiently even with large IMDb-like datasets.
* You can test with the `small` dataset for faster performance during development.

---

## 🏗️ util.py Overview

`util.py` contains helper classes used to manage the search frontier.

### Node

```python
class Node:
    def __init__(self, state, parent, action):
        self.state = state
        self.parent = parent
        self.action = action
```

Represents a state in the search tree:

* `state` = current actor
* `action` = movie that connects this actor to the previous one
* `parent` = previous Node

### StackFrontier (Depth-First Search)

Uses a **stack** (LIFO).
Useful for DFS but not for shortest paths.

### QueueFrontier (Breadth-First Search)

Uses a **queue** (FIFO).
Ensures we always find the **shortest connection** between actors.

---

## 🧾 Example CSV Format

Here’s what your dataset files should look like:

### people.csv

```
id,name,birth
1,Kevin Bacon,1958
2,Tom Hanks,1956
3,Meg Ryan,1961
```

### movies.csv

```
id,title,year
1,Apollo 13,1995
2,Sleepless in Seattle,1993
```

### stars.csv

```
person_id,movie_id
1,1
2,1
2,2
3,2
```

---

## 🏁 Credits

This project is based on **CS50’s Introduction to Artificial Intelligence with Python (Project 0)**.
Original specification: [CS50 AI Degrees of Separation](https://cs50.harvard.edu/ai/2020/projects/0/degrees/)

Created and adapted for learning and experimentation purposes.


