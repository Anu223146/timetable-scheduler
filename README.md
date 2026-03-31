# timetable-scheduler
 Academic timetable generator using Genetic Algorithm - Java BYOP Capstone
# 📅 Timetable Scheduler — Java BYOP Capstone

A **conflict-free academic timetable generator** built in Java using a **Genetic Algorithm**. Given a set of subjects, teachers, rooms, and time slots, the scheduler automatically produces a weekly timetable with zero conflicts.

---

## 🔍 Problem Statement

Academic institutions face a hard problem every semester: assigning subjects, teachers, and rooms to time slots without:
- Double-booking a teacher in two rooms at once
- Double-booking a room with two classes simultaneously
- Scheduling a teacher during their unavailable hours
- Assigning a lab session to a regular classroom

Manual timetabling is error-prone and time-consuming. This project automates it.

---

## 🧠 Approach — Genetic Algorithm

| Step | Description |
|------|-------------|
| **Chromosome** | A complete timetable (list of ScheduleEntry tuples) |
| **Fitness** | `1 / (1 + conflicts)` — perfect schedule = 1.0 |
| **Selection** | Tournament selection (k=5) |
| **Crossover** | Single-point crossover on the entry list |
| **Mutation** | Random slot/teacher/room replacement (rate=5%) |
| **Elitism** | Best individual always survives to next generation |

Runs for up to **500 generations** across a **population of 100** and stops early if a conflict-free schedule is found.

---

## 📁 Project Structure
```
TimetableScheduler/
├── Main.java               ← Entry point
├── DataSeeder.java         ← Sample academic data
├── Subject.java            ← Course model
├── Teacher.java            ← Faculty model
├── Room.java               ← Room/Lab model
├── TimeSlot.java           ← Time slot model
├── ScheduleEntry.java      ← One timetable row
├── Timetable.java          ← Full schedule + fitness
├── Scheduler.java          ← Interface (Strategy pattern)
├── GeneticScheduler.java   ← GA implementation
├── ConflictDetector.java   ← Conflict analysis utility
├── TimetableUI.java        ← Console display
└── TimetableExporter.java  ← CSV export
```

---

## ⚙️ Setup & Run

### Prerequisites
- Java 8 or later
- IntelliJ IDEA / Eclipse / VS Code or terminal

### Steps in IntelliJ
1. **File → New Project** → Java → Finish
2. Right-click `src` → **Mark Directory as → Sources Root**
3. Copy all `.java` files into `src/`
4. Right-click `Main.java` → **Run 'Main.main()'**

### Steps in Terminal
```bash
# Compile
javac -d out *.java

# Run
java -cp out Main
```

### Expected Output
```
+==========================================+
|      TIMETABLE SCHEDULER  v1.0          |
+==========================================+

Running Genetic Algorithm...

   Gen    0  |  fitness=0.3333  conflicts=2
   Gen   50  |  fitness=0.5000  conflicts=1
   Perfect schedule found at generation 87!

========== WEEKLY TIMETABLE ==========
...
Conflicts : 0
Fitness   : 1.0000
```

---

## 🔧 Customisation

Edit `DataSeeder.java` to add your own subjects, teachers, rooms, and time slots.

Tune GA parameters in `GeneticScheduler.java`:
```java
private static final int    POPULATION_SIZE = 100;
private static final int    GENERATIONS     = 500;
private static final double MUTATION_RATE   = 0.05;
private static final int    TOURNAMENT_SIZE = 5;
```

---

## 📚 Java Concepts Used

| Concept | Where Used |
|---------|-----------|
| OOP & Encapsulation | All model classes |
| Interfaces | `Scheduler.java` |
| Collections (List, Map, Set) | Throughout |
| Generics | `List<T>`, `Map<K,V>` |
| File I/O | `TimetableExporter.java` |
| Algorithm Design | Genetic Algorithm in `GeneticScheduler.java` |

---

## 👤 Author

anusha tiwari
Course: Programming in Java
reg no.-24bai10608

---

## 📄 License
MIT — free to use for educational purposes.
