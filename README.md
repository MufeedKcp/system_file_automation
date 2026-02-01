# System File Automation

## Overview

This repository contains **two related Python scripts** focused on **file system automation** using Python’s standard library (`os`). Together, they demonstrate practical, job‑relevant skills in:

* Directory and file inspection
* Path handling (relative vs absolute)
* File filtering by extension
* Safe directory creation
* File organization and movement
* Writing maintainable, ETL‑ready filesystem logic

These scripts are intentionally lightweight and dependency‑free, making them easy to run, test, and adapt for real‑world data engineering, backend, or automation workflows.

---

## Project Structure

```
.
├── incoming/          # Source directory for CSV processing
├── messy_file/        # Unorganized input files
├── organized/         # Auto-generated organized output
│   ├── CSV/
│   ├── PNG/
│   ├── PDF/
│   ├── text document/
│   └── others/
├── csv_etl_prep.py    # Script 1: CSV discovery & directory operations
├── file_organizer.py  # Script 2: File classification & movement
└── README.md
```
> by running this script will automatically create a folder callled organized and its subfolders
---

## Script 1: CSV Discovery & Directory Operations --os module.py

### Purpose

This script focuses on **exploring directories and preparing CSV files for ETL-style workflows**. It demonstrates how to safely inspect directories, identify valid files, and build a clean list of CSVs for downstream processing.

### Key Capabilities

* Lists directory contents (`os.listdir`)
* Reads and changes the working directory (`os.getcwd`, `os.chdir`)
* Distinguishes between files and folders
* Converts relative paths to absolute paths
* Filters files by extension (`.csv`, case-insensitive)
* Creates and removes directories safely
* Collects CSV file paths into a structured list

### Example Output

```text
CSV files to process:
['incoming/sales.csv', 'incoming/users.csv']
```

### Why This Matters

In production environments, data rarely arrives cleanly. This script mirrors **real ETL preparation steps** such as:

* Validating input directories
* Ignoring non-data files
* Building deterministic file lists for pipelines

---

## Script 2: File Organizer --file_organizer.py

### Purpose

This script automates the organization of a messy directory by **categorizing files based on type** and moving them into a clean, predictable folder structure.

### Key Capabilities

* Auto-creates a standardized directory tree
* Inspects files safely before moving them
* Classifies files by extension
* Handles unknown file types gracefully
* Uses clear, readable conditional logic

### File Routing Logic

| File Type | Destination Folder         |
| --------- | -------------------------- |
| `.csv`    | `organized/CSV/`           |
| `.txt`    | `organized/text document/` |
| `.pdf`    | `organized/PDF/`           |
| `.png`    | `organized/PNG/`           |
| Other     | `organized/others/`        |

### Why This Matters

This mirrors **real automation tasks** such as:

* Log cleanup
* Download folder organization
* Preprocessing data drops
* Ops / DevOps housekeeping scripts

---

## Skills Demonstrated

* Python standard library mastery (`os` module)
* Filesystem safety checks (`isfile`, `isdir`)
* Path construction using `os.path.join`
* Clean control flow and readable logic
* Automation mindset (repeatable, deterministic behavior)
* ETL and data‑engineering awareness

---

## How to Run

1. Ensure Python 3.x is installed
2. Create the required input folders:

   * `incoming/` (with `.csv` files)
   * `messy_file/` (with mixed file types)
3. Run each script:

```bash
python csv_etl_prep.py
python file_organizer.py
```

---

## Notes for Recruiters

* This project intentionally avoids external libraries to highlight **core Python competency**.
* The scripts are modular and easily extensible (e.g., logging, dry‑run mode, CLI arguments).
* Demonstrates readiness for junior data engineering, backend, automation, or scripting roles.

---

## Improvements will focus on :

* Add logging instead of `print`
* Support recursive directory traversal
* Add CLI arguments with `argparse`
* Implement unit tests
* Add rollback / dry‑run mode
