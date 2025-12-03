# Student-marks-analyzing-system
# -----------------------------------------
# Student Marks Analyzing System (Python)
# -----------------------------------------

students = {}
subjects = ["Maths", "Science", "English", "Social", "Computer"]

def add_student():
    student_id = input("Enter Student ID: ")
    name = input("Enter Student Name: ")
    students[student_id] = {"name": name, "marks": {}}
    print("Student added successfully!\n")

def enter_marks():
    student_id = input("Enter Student ID: ")
    if student_id not in students:
        print("Student not found!\n")
        return

  print("Enter marks for each subject (0–100):")
    for subject in subjects:
        mark = int(input(f"{subject}: "))
        students[student_id]["marks"][subject] = mark

  print("Marks entered successfully!\n")

def calculate_result(student_id):
    marks = students[student_id]["marks"].values()
    total = sum(marks)
    percentage = total / len(subjects)

  if percentage >= 90:
        grade = "A+"
    elif percentage >= 80:
        grade = "A"
    elif percentage >= 70:
        grade = "B"
    elif percentage >= 60:
        grade = "C"
    else:
        grade = "D"

  return total, percentage, grade

def view_report():
    student_id = input("Enter Student ID: ")
    if student_id not in students:
        print("Student not found!\n")
        return

  print("\n----- Student Report -----")
    print("Name:", students[student_id]["name"])
    print("ID:", student_id)
    print("---------------------------")

  for subject, mark in students[student_id]["marks"].items():
        print(f"{subject}: {mark}")

  total, percentage, grade = calculate_result(student_id)

  print("\nTotal Marks:", total)
    print("Percentage:", f"{percentage:.2f}%")
    print("Grade:", grade)
    print("---------------------------\n")

def show_menu():
    while True:
        print("===== Student Marks Analyzing System =====")
        print("1. Add Student")
        print("2. Enter Marks")
        print("3. View Report")
        print("4. Exit")
        choice = input("Enter your choice: ")

  if choice == "1":
            add_student()
        elif choice == "2":
            enter_marks()
        elif choice == "3":
            view_report()
        elif choice == "4":
            print("Exiting...")
            break
        else:
            print("Invalid choice! Try again.\n")

show_menu()
