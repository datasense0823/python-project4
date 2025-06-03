# 📦 DataSense Python Project 4: Event Planner & Guest Manager

## Objective

The goal of this project is to help you **apply Python fundamentals** in a real-world scenario using clean code and proper database integration. By the end, you will demonstrate:

- `print()` / `input()`
- Type conversion & validation
- Data structures: `list`, `tuple`, `dictionary`, `set`
- **Loops (for/while)** and **nested loops**
- **List comprehension**
- **Nested data handling**
- PostgreSQL integration using `psycopg2`

## ❓ Problem Statement

You’ve been hired by a growing event company to automate their **event and guest tracking process**. Your task is to build a command-line application that:

- Manages multiple events
- Handles multiple guests for each event
- Prevents duplicates
- Stores all data in a PostgreSQL database

But beyond basic functionality, the company wants a **robust solution**:
- Use of **loops** and **list comprehensions** to generate reports and summaries
- Handle **nested guest data structures**
- Efficient and reusable logic

## 🛠️ Step-by-Step Requirements

Welcome to DataSense Event Planner!

1. Create New Event

2. Add Guest to Event

3. View Guest List

4. Show RSVP Summary

5. Show Events with No Guests

6. Search Guest by Email

7. Exit

### 1️⃣ Create New Event

- Ask for: event name, date, location
- Store in `events` table
- Store inputs using correct types

### 2️⃣ Add Guest to Event

- Ask for: event ID, guest name, guest email, RSVP
- Insert guest only if not already in event
- Use dictionary to structure guest input:

Example: 

guest = {
    "name": name,
    "email": email,
    "rsvp": rsvp
}

### 3️⃣ View Guest List (with nested loops)

-Ask for event ID
-Fetch all guests
-Use for loop to display in formatted table

Bonus: Nest events with guest list

Example: 

for event in events:
    print(f"\nEvent: {event['event_name']}")
    for guest in event['guests']:
        print(f" - {guest['name']} ({guest['email']}) - RSVP: {guest['rsvp_status']}")

### 4️⃣ Show RSVP Summary

Fetch RSVP counts using list of guests

### 5️⃣ Events With No Guests


### 6️⃣ Search Guest by Email

- Ask for email
- Use SQL to find guest
- Print which event they're attending and their RSVP


### Postgres Schema

```sql
CREATE TABLE events (
    event_id SERIAL PRIMARY KEY,
    event_name VARCHAR(100),
    event_date DATE,
    location VARCHAR(100)
);

CREATE TABLE guests (
    guest_id SERIAL PRIMARY KEY,
    event_id INT REFERENCES events(event_id),
    name VARCHAR(100),
    email VARCHAR(100),
    rsvp_status VARCHAR(10),
    UNIQUE (event_id, email)
);

```

### 📁 Folder Structure

```
event_planner/
├── main.py              # Menu logic and program entry
├── db.py                # DB connection, SQL helper functions
├── models.py            # Event & Guest logic
├── utils.py             # Validations, list comprehension logic
└── requirements.txt     # psycopg2, etc.
```


### Examples

### 1. RSVP Summary Output:

Event: Tech Conference 2025
Total Guests: 5
Confirmed: 3
Maybe: 1
Declined: 1

### 2. Events With No Guests:

Found 2 events with no guests:
- Hackathon Finals
- Startup Expo

### Candidate Submission Checklist

Must Include:

1. All Python files: main.py, db.py, models.py, utils.py
2. PostgreSQL .sql file for schema
3. Screenshot(s) of:

Event creation,Adding guests, RSVP summary,Events with no guests

4. Your own README.md describing your learnings and logic

## 🎓 Evaluation Rubric

```
Area                          Points
----------------------------  -------
Python Concepts Applied       25
List Comprehension & Loops    20
DB Integration (Postgres)     20
Output Formatting & Flow      15
Code Organization             10
Bonus Features                10
```

# 🔐 Rules
1. Stick to core Python only (no frameworks or AI).
2. Use PostgreSQL only, not SQLite/MySQL.
3. Code should be readable and modularized.


**Happy coding!**
Team DataSense






