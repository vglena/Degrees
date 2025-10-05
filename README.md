🎬 Degrees of Separation (CS50 AI Project 0)

This program determines the degrees of separation between two actors based on the movies they have starred in together.
It finds the shortest connection (if any) using a Breadth-First Search (BFS) algorithm.

📖 Overview

Given a dataset of actors, movies, and their relationships (from IMDb), the program builds a network graph where:

Nodes represent people (actors).

Edges represent shared movies between actors.

When you input two actor names, it calculates the shortest path between them — showing through which movies and co-stars they are connected.

For example:
Name: Tom Hanks
Name: Emma Watson
4 degrees of separation.
1: Tom Hanks and Gary Sinise starred in Forrest Gump
2: Gary Sinise and Kevin Bacon starred in Apollo 13
3: Kevin Bacon and Daniel Radcliffe starred in A Few Good Men
4: Daniel Radcliffe and Emma Watson starred in Harry Potter and the Sorcerer’s Stone
