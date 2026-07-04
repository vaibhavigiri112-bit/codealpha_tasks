# codealpha_tasks
import json
import os

FILE = "students.json"

def load_students():
    if os.path.exists(FILE):
        with open(FILE, "r") as f:
            return json.load(f)
    return []

def save_students(students):
    with open(FILE, "w") as f:
        json.dump(students, f, indent=4)

def add_student(students):
    roll = input("Enter Roll Number: ")
    name = input("Enter Name: ")
    age = input("Enter Age: ")
    course = input("Enter Course: ")

    students.append({
        "Roll": roll,
        "Name": name,
        "Age": age,
        "Course": course
    })

    save_students(students)
    print("Student added successfully!")

def view_students(students):
    if not students:
        print("No student records found.")
        return

    for s in students:
        print("-------------------------")
        print("Roll:", s["Roll"])
        print("Name:", s["Name"])
        print("Age:", s["Age"])
        print("Course:", s["Course"])

def search_student(students):
    roll = input("Enter Roll Number: ")

    for s in students:
        if s["Roll"] == roll:
            print(s)
            return

    print("Student not found.")

def update_student(students):
    roll = input("Enter Roll Number: ")

    for s in students:
        if s["Roll"] == roll:
            s["Name"] = input("New Name: ")
            s["Age"] = input("New Age: ")
            s["Course"] = input("New Course: ")
            save_students(students)
            print("Student updated successfully!")
            return

    print("Student not found.")

def delete_student(students):
    roll = input("Enter Roll Number: ")

    for s in students:
        if s["Roll"] == roll:
            students.remove(s)
            save_students(students)
            print("Student deleted successfully!")
            return

    print("Student not found.")

def main():
    students = load_students()

    while True:
        print("\n===== Student Management System =====")
        print("1. Add Student")
        print("2. View Students")
        print("3. Search Student")
        print("4. Update Student")
        print("5. Delete Student")
        print("6. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            add_student(students)
        elif choice == "2":
            view_students(students)
        elif choice == "3":
            search_student(students)
        elif choice == "4":
            update_student(students)
        elif choice == "5":
            delete_student(students)
        elif choice == "6":
            print("Thank you!")
            break
        else:
            print("Invalid choice!")

if __name__ == "__main__":
    main()


# Student Management System

A simple Python-based Student Management System.

## Features
- Add Student
- View Students
- Search Student
- Update Student
- Delete Student
- Data stored in JSON file

## Requirements
- Python 3.x

## Run

python main.py
