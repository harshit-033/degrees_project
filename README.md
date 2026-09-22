# Degrees of Separation

## Overview

This project finds the shortest chain of film collaborations connecting two people. It models the data as a graph in which people are connected when they appeared in the same movie.

Given two actor names, the program searches for the shortest sequence of co-starring relationships and prints the movies that connect each pair.

## How It Works

The program loads three CSV files:

- `people.csv` — person IDs, names, and birth years.
- `movies.csv` — movie IDs, titles, and release years.
- `stars.csv` — relationships between people and movies.

The data is stored in memory as mappings between people and movies. A person can be connected to other people through any movie they share.

The shortest-path search uses breadth-first search (BFS). Each search node stores the current person, its parent node, and the movie that produced the connection. This allows the final path to be reconstructed once the target person is found.

When a name matches multiple people, the program displays the available IDs and birth years so the intended person can be selected.

## Project Structure

| File | Purpose |
| --- | --- |
| `degrees.py` | Loads the movie database, resolves people, finds neighbors, and performs the shortest-path search. |
| `util.py` | Provides search-node, stack-frontier, and queue-frontier implementations. |
| `small/` | Small sample movie database for testing. |
| `large/` | Larger movie database for broader searches. |

## Key Concepts

- Graph representation
- Breadth-first search
- Shortest-path reconstruction
- Relationship mapping
- Ambiguous-name resolution
- CSV data processing

## Running

```bash
python degrees.py [directory]
```

When no directory is supplied, the program uses the `large` dataset.

The program then asks for a source person and a target person and reports the shortest connection between them.

## Output

For a successful search, the program reports:

- The number of degrees of separation.
- Each pair of people in the path.
- The movie through which the pair is connected.

If no connection exists in the loaded data, the program reports that the two people are not connected.
