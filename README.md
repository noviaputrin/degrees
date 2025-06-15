# 🎬 Degrees of Separation

A command-line tool that determines how many "degrees of separation" exist between two actors, based on the movies they’ve co-starred in.

## 🔍 Description
This program models the famous [Six Degrees of Kevin Bacon](https://en.wikipedia.org/wiki/Six_Degrees_of_Kevin_Bacon) game, which posits that any two actors can be connected through six or fewer mutual film roles. Using breadth-first search (BFS), this tool finds the shortest connection path between any two actors via shared movie appearances.

```
$ python degrees.py large
Loading data...
Data loaded.
Name: Emma Watson
Name: Jennifer Lawrence
3 degrees of separation.
1: Emma Watson and Brendan Gleeson starred in Harry Potter and the Order of the Phoenix
2: Brendan Gleeson and Michael Fassbender starred in Trespass Against Us
3: Michael Fassbender and Jennifer Lawrence starred in X-Men: First Class
```

## 📂 Datasets
The program supports two datasets: ```small``` and ```large```. Each dataset folder includes the following files:

```people.csv```: Contains actor information
```id```, ```name```, ```birth```
```movies.csv```: Contains movie information
```id```, ```title```, ```year```
```stars.csv```: Maps actors to the movies they starred in
```person_id```, ```movie_id```

**Example**

If ```stars.csv``` contains:
```
102,104257
```
Then Kevin Bacon (ID ```102```) starred in _A Few Good Men_ (ID ```104257```), which can be confirmed using the corresponding entries in ```people.csv``` and ```movies.csv```.

## 🧠 How It Works
The program constructs a graph where:

* **Nodes** represent actors
* **Edges** represent co-starring in a film

It performs **BFS** to explore the shortest path between two actors:

* Each level of search expands to all co-stars of the current actor
* Paths are tracked to return the list of actors and movies involved

## 🚀 Getting Started
**Prerequisites**
* Python 3.x

**Running the Program**
```
$ python degrees.py [dataset]
```
**Example:**
```
$ python degrees.py small
```

You’ll be prompted to enter two actor names, and the program will return the shortest connection between them.

## 📁 File Structure
```
├── degrees.py
├── util.py
├── small/
│   ├── people.csv
│   ├── movies.csv
│   └── stars.csv
├── large/
│   ├── people.csv
│   ├── movies.csv
│   └── stars.csv
```

## ✅ Features

* Accurate actor lookup with name disambiguation
* Fast search using breadth-first algorithm
* Scalable to large datasets
* Modular and easy to read codebase

## 🧪 Example Queries

* Kevin Bacon → Tom Hanks
* Emma Watson → Daniel Radcliffe
* Chris Pratt → Zoe Saldana