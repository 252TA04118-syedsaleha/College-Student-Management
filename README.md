#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 100
#define MAX_FACULTY 50
#define MAX_COURSES 20

struct Student {
    int rollNo;
    char name[50];
    char department[30];
    int year;
    int age;
    char gender[10];
    float attendance;
    float marks;
};

struct Faculty {
    int id;
    char name[50];
    char department[30];
    char subject[40];
};

struct Course {
    int courseId;
    char courseName[50];
    char department[30];
    int credits;
};

struct Student students[MAX_STUDENTS];
struct Faculty faculty[MAX_FACULTY];
struct Course courses[MAX_COURSES];

int studentCount = 0;
int facultyCount = 0;
int courseCount = 0;


/* Function to add student */
void addStudent() {

    if (studentCount >= MAX_STUDENTS) {
        printf("\nStudent limit reached!\n");
        return;
    }

    printf("\n========== ADD STUDENT ==========\n");

    printf("Enter Roll Number: ");
    scanf("%d", &students[studentCount].rollNo);

    printf("Enter Student Name: ");
    scanf(" %[^\n]", students[studentCount].name);

    printf("Enter Department: ");
    scanf(" %[^\n]", students[studentCount].department);

    printf("Enter Year: ");
    scanf("%d", &students[studentCount].year);

    printf("Enter Age: ");
    scanf("%d", &students[studentCount].age);

    printf("Enter Gender: ");
    scanf("%s", students[studentCount].gender);

    printf("Enter Attendance Percentage: ");
    scanf("%f", &students[studentCount].attendance);

    printf("Enter Marks: ");
    scanf("%f", &students[studentCount].marks);

    studentCount++;

    printf("\nStudent added successfully!\n");
}


/* Function to display students */
void displayStudents() {

    int i;

    if (studentCount == 0) {
        printf("\nNo student records available.\n");
        return;
    }

    printf("\n========== STUDENT RECORDS ==========\n");

    for (i = 0; i < studentCount; i++) {

        printf("\n--------------------------------------\n");
        printf("Roll Number : %d\n", students[i].rollNo);
        printf("Name        : %s\n", students[i].name);
        printf("Department  : %s\n", students[i].department);
        printf("Year        : %d\n", students[i].year);
        printf("Age         : %d\n", students[i].age);
        printf("Gender      : %s\n", students[i].gender);
        printf("Attendance  : %.2f%%\n", students[i].attendance);
        printf("Marks       : %.2f\n", students[i].marks);
    }
}


/* Function to search student */
void searchStudent() {

    int roll;
    int i;
    int found = 0;

    printf("\nEnter Roll Number: ");
    scanf("%d", &roll);

    for (i = 0; i < studentCount; i++) {

        if (students[i].rollNo == roll) {

            printf("\n========== STUDENT FOUND ==========\n");

            printf("Roll Number : %d\n", students[i].rollNo);
            printf("Name        : %s\n", students[i].name);
            printf("Department  : %s\n", students[i].department);
            printf("Year        : %d\n", students[i].year);
            printf("Age         : %d\n", students[i].age);
            printf("Gender      : %s\n", students[i].gender);
            printf("Attendance  : %.2f%%\n", students[i].attendance);
            printf("Marks       : %.2f\n", students[i].marks);

            found = 1;
            break;
        }
    }

    if (!found) {
        printf("\nStudent not found!\n");
    }
}


/* Function to add faculty */
void addFaculty() {

    if (facultyCount >= MAX_FACULTY) {
        printf("\nFaculty limit reached!\n");
        return;
    }

    printf("\n========== ADD FACULTY ==========\n");

    printf("Enter Faculty ID: ");
    scanf("%d", &faculty[facultyCount].id);

    printf("Enter Faculty Name: ");
    scanf(" %[^\n]", faculty[facultyCount].name);

    printf("Enter Department: ");
    scanf(" %[^\n]", faculty[facultyCount].department);

    printf("Enter Subject: ");
    scanf(" %[^\n]", faculty[facultyCount].subject);

    facultyCount++;

    printf("\nFaculty added successfully!\n");
}


/* Function to display faculty */
void displayFaculty() {

    int i;

    if (facultyCount == 0) {
        printf("\nNo faculty records available.\n");
        return;
    }

    printf("\n========== FACULTY RECORDS ==========\n");

    for (i = 0; i < facultyCount; i++) {

        printf("\n--------------------------------------\n");
        printf("Faculty ID  : %d\n", faculty[i].id);
        printf("Name        : %s\n", faculty[i].name);
        printf("Department  : %s\n", faculty[i].department);
        printf("Subject     : %s\n", faculty[i].subject);
    }
}


/* Function to add course */
void addCourse() {

    if (courseCount >= MAX_COURSES) {
        printf("\nCourse limit reached!\n");
        return;
    }

    printf("\n========== ADD COURSE ==========\n");

    printf("Enter Course ID: ");
    scanf("%d", &courses[courseCount].courseId);

    printf("Enter Course Name: ");
    scanf(" %[^\n]", courses[courseCount].courseName);

    printf("Enter Department: ");
    scanf(" %[^\n]", courses[courseCount].department);

    printf("Enter Credits: ");
    scanf("%d", &courses[courseCount].credits);

    courseCount++;

    printf("\nCourse added successfully!\n");
}


/* Function to display courses */
void displayCourses() {

    int i;

    if (courseCount == 0) {
        printf("\nNo course records available.\n");
        return;
    }

    printf("\n========== COURSE RECORDS ==========\n");

    for (i = 0; i < courseCount; i++) {

        printf("\n--------------------------------------\n");
        printf("Course ID   : %d\n", courses[i].courseId);
        printf("Course Name : %s\n", courses[i].courseName);
        printf("Department  : %s\n", courses[i].department);
        printf("Credits     : %d\n", courses[i].credits);
    }
}


/* Function to display top student */
void topStudent() {

    int i;
    int top = 0;

    if (studentCount == 0) {
        printf("\nNo student records available.\n");
        return;
    }

    for (i = 1; i < studentCount; i++) {

        if (students[i].marks > students[top].marks) {
            top = i;
        }
    }

    printf("\n========== TOP STUDENT ==========\n");
    printf("Name       : %s\n", students[top].name);
    printf("Roll No    : %d\n", students[top].rollNo);
    printf("Department : %s\n", students[top].department);
    printf("Marks      : %.2f\n", students[top].marks);
}


/* Function to display attendance report */
void attendanceReport() {

    int i;

    if (studentCount == 0) {
        printf("\nNo student records available.\n");
        return;
    }

    printf("\n========== ATTENDANCE REPORT ==========\n");

    for (i = 0; i < studentCount; i++) {

        printf("\nName       : %s", students[i].name);
        printf("\nRoll No    : %d", students[i].rollNo);
        printf("\nAttendance : %.2f%%", students[i].attendance);

        if (students[i].attendance >= 75) {
            printf("\nStatus     : Eligible");
        } else {
            printf("\nStatus     : Short Attendance");
        }

        printf("\n--------------------------------------\n");
    }
}


/* Function to display marks report */
void marksReport() {

    int i;

    if (studentCount == 0) {
        printf("\nNo student records available.\n");
        return;
    }

    printf("\n========== MARKS REPORT ==========\n");

    for (i = 0; i < studentCount; i++) {

        printf("\nName  : %s", students[i].name);
        printf("\nRoll  : %d", students[i].rollNo);
        printf("\nMarks : %.2f", students[i].marks);

        if (students[i].marks >= 90)
            printf("\nGrade : A+");
        else if (students[i].marks >= 80)
            printf("\nGrade : A");
        else if (students[i].marks >= 70)
            printf("\nGrade : B");
        else if (students[i].marks >= 60)
            printf("\nGrade : C");
        else if (students[i].marks >= 50)
            printf("\nGrade : D");
        else
            printf("\nGrade : F");

        printf("\n--------------------------------------\n");
    }
}


/* Main function */
int main() {

    int choice;

    printf("============================================\n");
    printf("        COLLEGE MANAGEMENT SYSTEM\n");
    printf("============================================\n");

    do {

        printf("\n\n=============== MAIN MENU ===============\n");
        printf("1.  Add Student\n");
        printf("2.  Display Students\n");
        printf("3.  Search Student\n");
        printf("4.  Add Faculty\n");
        printf("5.  Display Faculty\n");
        printf("6.  Add Course\n");
        printf("7.  Display Courses\n");
        printf("8.  Find Top Student\n");
        printf("9.  Attendance Report\n");
        printf("10. Marks and Grade Report\n");
        printf("11. Exit\n");
        printf("=========================================\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {

            case 1:
                addStudent();
                break;

            case 2:
                displayStudents();
                break;

            case 3:
                searchStudent();
                break;

            case 4:
                addFaculty();
                break;

            case 5:
                displayFaculty();
                break;

            case 6:
                addCourse();
                break;

            case 7:
                displayCourses();
                break;

            case 8:
                topStudent();
                break;

            case 9:
                attendanceReport();
                break;

            case 10:
                marksReport();
                break;

            case 11:
                printf("\nThank you for using College Management System!\n");
                break;

            default:
                printf("\nInvalid choice! Please enter a valid option.\n");
        }

    } while (choice != 11);

    return 0;
}
