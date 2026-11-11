# Practical 8 – Python & SQLite (Student Database)

Connects Python to an **SQLite** database using the built-in `sqlite3` module, creates a `students` table and inserts a student record.

## Table schema

| Column    | Type    | Constraints                          |
|-----------|---------|--------------------------------------|
| `id`      | INTEGER | PRIMARY KEY, AUTOINCREMENT           |
| `name`    | TEXT    | NOT NULL                             |
| `roll_no` | TEXT    | UNIQUE, NOT NULL                     |
| `marks`   | REAL    | CHECK(marks >= 0 AND marks <= 100)   |

## Files

```
Practical-8/
├── main.py         # connects, creates table, inserts a record
├── sqlconnect.py   # same flow, plus closes the connection
├── students.db     # SQLite database (already contains one student record)
├── .gitignore
└── README.md
```

`students.db` is included and already holds the record for roll no `39`. If it is missing, a script creates it automatically.

## Requirements

Python 3.8+ (`sqlite3` ships with Python, so there is nothing to install).

## Run

```bash
python3 sqlconnect.py
```

Expected output on a fresh database (no `students.db`):

```
Database connected successfully!
Student record added successfully!
Students table created successfully!
```

> **Note:** the included `students.db` already contains roll no `39`, and `roll_no`
> is `UNIQUE`, so running a script again raises `sqlite3.IntegrityError`.
> To re-run, delete `students.db` first and the script will recreate it.

## View the data

```bash
sqlite3 students.db "SELECT * FROM students;"
```
