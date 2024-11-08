import numpy as np

class StudentGradeTracker:
    def __init__(self):
        self.users = {"admin": "admin123"}
        self.logged_in_user = None
        self.students = {}
        self.courses = {}

    # Login system
    def login(self, username, password):
        if username in self.users and self.users[username] == password:
            self.logged_in_user = username
            print(f"Welcome {username}!")
        else:
            print("Invalid username or password.")

    # Dashboard overview
    def dashboard(self):
        if self.logged_in_user:
            print("\nDashboard Overview")
            print("------------------")
            print("1. Add Student")
            print("2. Add Course")
            print("3. Add Grade")
            print("4. Display Grades")
            print("5. Logout")
            choice = input("Enter your choice: ")
            if choice == '1':
                self.add_student()
            elif choice == '2':
                self.add_course()
            elif choice == '3':
                self.add_grade()
            elif choice == '4':
                self.display_all_grades()
            elif choice == '5':
                self.logout()
            else:
                print("Invalid choice. Please try again.")
        else:
            print("Please log in first.")

    # Adding a new student
    def add_student(self):
        if self.logged_in_user:
            name = input("Enter student name: ")
            if name not in self.students:
                self.students[name] = {}
                print(f"Student {name} added.")
            else:
                print(f"Student {name} already exists.")
        else:
            print("Please log in first.")

    # Adding a new course
    def add_course(self):
        if self.logged_in_user:
            course = input("Enter course name: ")
            if course not in self.courses:
                self.courses[course] = []
                print(f"Course {course} added.")
            else:
                print(f"Course {course} already exists.")
        else:
            print("Please log in first.")

    # Adding a grade for a student in a specific course
    def add_grade(self):
        if self.logged_in_user:
            name = input("Enter student name: ")
            course = input("Enter course name: ")
            grade = float(input("Enter grade: "))

            if name in self.students:
                if course in self.courses:
                    if course not in self.students[name]:
                        self.students[name][course] = []
                    self.students[name][course].append(grade)
                    print(f"Grade {grade} added for {name} in {course}.")
                else:
                    print(f"Course {course} does not exist.")
            else:
                print(f"Student {name} does not exist.")
        else:
            print("Please log in first.")

    # Calculating average grade for a student in a specific course
    def get_average_grade(self, name, course):
        if name in self.students and course in self.students[name]:
            grades = np.array(self.students[name][course])
            return np.mean(grades)
        else:
            print(f"Course {course} for student {name} does not exist.")
            return None

    # Displaying all grades and averages for all students
    def display_all_grades(self):
        if self.logged_in_user:
            for name, courses in self.students.items():
                print(f"\nStudent: {name}")
                for course, grades in courses.items():
                    avg_grade = self.get_average_grade(name, course)
                    print(f"  Course: {course}, Grades: {grades}, Average Grade: {avg_grade:.2f}")
        else:
            print("Please log in first.")

    # Logging out the current user
    def logout(self):
        print(f"Goodbye, {self.logged_in_user}!")
        self.logged_in_user = None

# Example usage
tracker = StudentGradeTracker()

# Simulating login
tracker.login("admin", "admin123")
tracker.dashboard()  # Invoke the dashboard method to display options

# The code expects the user to interact via input in a real-world scenario.
# This block can be expanded or modified to simulate different actions.
