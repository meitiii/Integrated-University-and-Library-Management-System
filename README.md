# Integrated University and Library Management System

This project is a comprehensive database management system for an educational institution, covering two main areas: **Education** and **Library**. The system is designed and implemented using SQL Server and includes tables, stored procedures, functions, and triggers to efficiently manage academic and library-related data and processes.

## 🏛️ Database Architecture

The database is divided into two primary schemas:

### 1. `Education` Schema
This section is responsible for managing all academic aspects of the university.
* **Core Information Management**: Manages buildings, departments, and academic majors.
* **Student and Instructor Management**: Handles the registration of individuals, assignment of advisors, and management of personal information.
* **Course and Section Management**: Defines courses, prerequisites, course offerings in different semesters, and academic charts.
* **Academic Processes**: Manages course registration, grade submission, GPA calculation, and student academic status checks.

### 2. `Library` Schema
This section is designed to fully manage all library processes.
* **Resource Management**: Manages book categories, publisher information, and different editions of books.
* **Account Management**: Creates library accounts for students and instructors.
* **Library Processes**: Handles book borrowing, returns, due date extensions, and management of overdue fines.
* **Book Recommendation System**: Provides book recommendations to users based on their borrowing history and that of similar users.

---

## ✨ Core Features and Capabilities

### Functions
The system includes various functions for complex calculations and data retrieval:
* **`Education.TermGPA`**: Calculates a student's GPA for a specific term.
* **`Education.totalGPA`**: Calculates a student's overall GPA.
* **`Education.SuggestCoursesForStudent`**: Suggests available courses for a student based on their academic chart and passed courses.
* **`Education.Weeklyschedule`**: Displays a student's weekly schedule for the current semester.
* **`Library.GetRecommendedBooks`**: Recommends books to a student based on their borrowing history and that of users with similar tastes.
* **`Library.getTotalFineByStuID`**: Calculates the total outstanding fines for a student.

### Stored Procedures
Stored procedures encapsulate the main database operations and implement the system's business logic:
* **`Education.addPerson`**: Adds a new person (student, instructor, or librarian) to the system.
* **`Education.takeSection`**: Manages the course registration process for a student, checking for prerequisites, section capacity, and time conflicts.
* **`Education.updateStudentGrade`**: Updates a student's grade for a course and determines their pass/fail status.
* **`Library.borrowBook`**: Records the process of borrowing a book, checking for availability and account status.
* **`Library.returnBook`**: Records a book return and automatically applies a fine if it is overdue.
* **`Library.payFinesByFineIdAndAccID`**: Processes the payment of a student's fines.

### Triggers
Triggers are used to automate processes and maintain data integrity:
* **`trgAfterAddPerson`**: Automatically creates a library account when a new person is added to the system.
* **`trgReturnBook`**: Automatically creates a fine record if a book is returned after its due date.
* **`checkGraduation`**: Checks the student's academic status after each grade update and sets their status to "Graduated" if they have completed the required credits.
* **`trgLimitBorrow`**: Prevents a user from borrowing more than three books simultaneously.
* **Logging Triggers**: All major DML operations (INSERT, UPDATE, DELETE) are logged to track changes and ensure accountability.

---

## User Management and Access Control

The system features three distinct access levels to ensure data security:
* **`AdminRole`**: This role has full access to manage educational data, such as adding users, defining courses, and other administrative tasks.
* **`LibrarianRole`**: This role has access to library-related processes, such as recording borrowed and returned books.
* **`StudentRole`**: This role allows students to perform actions related to their academic progress, such as course registration and viewing grades, schedules, and GPAs.

A separate login is defined for each role at the server level to enforce these permissions.

---

## 🚀 Usage and Testing Guide

The `data sample.sql` file contains a comprehensive set of sample data for all parts of the system, including departments, majors, courses, instructors, students, and books.

This file also includes extensive test scenarios to demonstrate the system's functionality, such as:
* A complete 8-semester scenario for a student, including course registration, failing a course, retaking it, and finally graduating.
* Examples of library processes like borrowing, returning, extending due dates, and paying fines.
* Calls to automated procedures like `autoTakeSection` for automatic course registration and `autoFillGrade` for randomly assigning grades to test the system at scale.

## Developers

* [Arian Wahedzadegan](https://github.com/Arian84aw)
* [Mahdi Fekri](https://github.com/meitiii)

This project was completed for the Data Base course under the supervision of Dr. Shirin Baghoolizadeh.
