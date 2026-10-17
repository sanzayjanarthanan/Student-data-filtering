# Task 8: Simple Data Filtering

## Table of Contents
- [Description](#description)
- [Objective](#objective)
- [Tools Used](#tools-used)
- [Dataset](#dataset)
- [Filtering Operations](#filtering-operations)
- [Code](#code)
- [Output](#output)
- [Pandas Version](#pandas-version)
- [How to Run](#how-to-run)
- [Project Structure](#project-structure)
- [Key Learnings](#key-learnings)
- [Interview Questions](#interview-questions)
- [Author](#author)

## Description
A Python program that creates a collection of student records and filters students based on **marks, age, and department** using conditional logic.

## Objective
Understand how conditions can be used to filter structured data.

## Tools Used
- Python
- Jupyter Notebook
- Pandas (bonus section)

## Dataset
Manually created student records, stored as a **list of dictionaries**.

| Name | Age | Marks | Department |
|------|-----|-------|------------|
| Arun | 20 | 88 | AI&DS |
| Divya | 19 | 72 | CSE |
| Karthik | 21 | 91 | AI&DS |
| Meena | 20 | 65 | ECE |
| Rahul | 22 | 54 | CSE |
| Sneha | 19 | 79 | AI&DS |
| Vikram | 21 | 83 | ECE |

## Filtering Operations
| # | Condition | Description |
|---|-----------|-------------|
| 1 | `marks > 80` | High scorers |
| 2 | `department == "AI&DS"` | Department-wise filter |
| 3 | `age < 21` | Age-based filter |
| 4 | `department == "AI&DS" and marks > 80` | Combined (AND) condition |

## Code

```python
students = [
    {"name": "Arun",    "age": 20, "marks": 88, "department": "AI&DS"},
    {"name": "Divya",   "age": 19, "marks": 72, "department": "CSE"},
    {"name": "Karthik", "age": 21, "marks": 91, "department": "AI&DS"},
    {"name": "Meena",   "age": 20, "marks": 65, "department": "ECE"},
    {"name": "Rahul",   "age": 22, "marks": 54, "department": "CSE"},
    {"name": "Sneha",   "age": 19, "marks": 79, "department": "AI&DS"},
    {"name": "Vikram",  "age": 21, "marks": 83, "department": "ECE"},
]

def show(title, records):
    print(f"\n{title}")
    print("-" * len(title))
    if not records:
        print("No students found.")
    for s in records:
        print(f"{s['name']:<8} | Age: {s['age']} | Marks: {s['marks']} | Dept: {s['department']}")

# Filter 1: marks above 80
high_scorers = [s for s in students if s["marks"] > 80]
show("Students with marks > 80", high_scorers)

# Filter 2: department is AI&DS
ads_students = [s for s in students if s["department"] == "AI&DS"]
show("Students from AI&DS", ads_students)

# Filter 3: age below 21
young = [s for s in students if s["age"] < 21]
show("Students with age < 21", young)

# Filter 4: combined condition
combo = [s for s in students if s["department"] == "AI&DS" and s["marks"] > 80]
show("AI&DS students with marks > 80", combo)
```

## Output

```
Students with marks > 80
------------------------
Arun     | Age: 20 | Marks: 88 | Dept: AI&DS
Karthik  | Age: 21 | Marks: 91 | Dept: AI&DS
Vikram   | Age: 21 | Marks: 83 | Dept: ECE

Students from AI&DS
-------------------
Arun     | Age: 20 | Marks: 88 | Dept: AI&DS
Karthik  | Age: 21 | Marks: 91 | Dept: AI&DS
Sneha    | Age: 19 | Marks: 79 | Dept: AI&DS

Students with age < 21
----------------------
Arun     | Age: 20 | Marks: 88 | Dept: AI&DS
Divya    | Age: 19 | Marks: 72 | Dept: CSE
Meena    | Age: 20 | Marks: 65 | Dept: ECE
Sneha    | Age: 19 | Marks: 79 | Dept: AI&DS

AI&DS students with marks > 80
------------------------------
Arun     | Age: 20 | Marks: 88 | Dept: AI&DS
Karthik  | Age: 21 | Marks: 91 | Dept: AI&DS
```

## Pandas Version

```python
import pandas as pd

df = pd.DataFrame(students)

print(df[df["marks"] > 80])
print(df[(df["department"] == "AI&DS") & (df["age"] < 21)])
```

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/sanzayjanarthanan/<repo-name>.git
   cd <repo-name>
   ```
2. Install dependencies:
   ```bash
   pip install pandas jupyter
   ```
3. Open the notebook:
   ```bash
   jupyter notebook task8_data_filtering.ipynb
   ```
4. Run all cells (Cell → Run All).

## Project Structure
```
.
├── task8_data_filtering.ipynb   # Notebook with code and outputs
├── README.md                    # Project documentation
└── Task8_Project_Report.docx    # Project report (optional)
```

## Key Learnings
- Filtering selects a subset of records without changing the original data.
- List comprehensions with conditions give clean, readable filters.
- Multiple conditions combine with `and` / `or` (`&` / `|` in Pandas).
- Filtering reduces rows; sorting only changes their order.

## Interview Questions
**What is data filtering?**
Selecting only the records that satisfy a given condition, without modifying the original data.

**How would you filter a Pandas DataFrame?**
Using boolean indexing, e.g. `df[df["marks"] > 80]`. For multiple conditions use `&` / `|` with each condition in brackets.

**What is the difference between filtering and sorting?**
Filtering reduces the number of rows (returns a subset). Sorting only rearranges the order; the row count stays the same.

## Author
**J Sanjay**
AI & Data Science Student, Velammal Institute of Technology, Chennai
GitHub: [sanzayjanarthanan](https://github.com/sanzayjanarthanan)
