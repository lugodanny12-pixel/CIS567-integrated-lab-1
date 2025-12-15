# CIS567-integrated-lab-1
Week 5 Assignment
import sys

# Step 1: Read student status
status = input().strip()

# Validate status
if status not in ("UG", "G", "DL"):
    print("Error: student status must be UG, G or DL")
    sys.exit()

# Read scores (homework, quizzes, midterm, final exam)
homework_pts, quizzes_pts, midterm_pts, final_pts = map(float, input().split())

# Max points
MAX_HOMEWORK = 800.0
MAX_QUIZZES = 400.0
MAX_MIDTERM = 150.0
MAX_FINAL = 200.0

# Calculate percentages
homework = (homework_pts / MAX_HOMEWORK) * 100.0
quizzes = (quizzes_pts / MAX_QUIZZES) * 100.0
midterm = (midterm_pts / MAX_MIDTERM) * 100.0
final_exam = (final_pts / MAX_FINAL) * 100.0

# Step 2: Cap at 100%
if homework > 100.0:
    homework = 100.0
if quizzes > 100.0:
    quizzes = 100.0
if midterm > 100.0:
    midterm = 100.0
if final_exam > 100.0:
    final_exam = 100.0

# Output category averages
print(f"Homework: {homework:0.1f}%")
print(f"Quizzes: {quizzes:0.1f}%")
print(f"Midterm: {midterm:0.1f}%")
print(f"Final Exam: {final_exam:0.1f}%")

# Step 3: Compute course average based on status
if status == "UG":
    course_avg = (homework * 0.20 +
                  quizzes * 0.20 +
                  midterm * 0.30 +
                  final_exam * 0.30)
elif status == "G":
    course_avg = (homework * 0.15 +
                  quizzes * 0.05 +
                  midterm * 0.35 +
                  final_exam * 0.45)
else:  # DL
    course_avg = (homework * 0.05 +
                  quizzes * 0.05 +
                  midterm * 0.40 +
                  final_exam * 0.50)

print(f"{status} average: {course_avg:0.1f}%")

# Step 4: Determine letter grade
if course_avg >= 90.0:
    letter = "A"
elif course_avg >= 80.0:
    letter = "B"
elif course_avg >= 70.0:
    letter = "C"
elif course_avg >= 60.0:
    letter = "D"
else:
    letter = "F"

print(f"Course grade: {letter}")
