## Flowchart:
https://drive.google.com/file/d/1pRYa1cdhLMxFJiyRFp_fIUAOMhA_DuMt/view?usp=sharing

## Challenges:
I kept on forgetting to call super.printInfo() in the derived class, so my base info wasn't printing.

## Video:

## Code:
    public class Course {
       // Private fields for course information
       private String courseNumber;
       private String courseTitle;
    
       // Setter for course number
       public void setCourseNumber(String number) {
          courseNumber = number;
       }
    
       // Setter for course title
       public void setCourseTitle(String title) {
          courseTitle = title;
       }
    
       // Getter for course number
       public String getCourseNumber() {
          return courseNumber;
       }
    
       // Getter for course title
       public String getCourseTitle() {
          return courseTitle;
       }
    
       // Print course info
       public void printInfo() {
          System.out.println("Course Information:");
          System.out.println("   Course Number: " + courseNumber);
          System.out.println("   Course Title: " + courseTitle);
       }
    }
    // ===== end =====
    
    
    // ===== Code from file OfferedCourse.java =====
    public class OfferedCourse extends Course {
       // Additional fields for offered courses
       private String instructorName;
       private String location;
       private String classTime;
    
       // Setters for new fields
       public void setInstructorName(String name) {
          instructorName = name;
       }
    
       public void setLocation(String loc) {
          location = loc;
       }
    
       public void setClassTime(String time) {
          classTime = time;
       }
    
       // Getters for new fields
       public String getInstructorName() {
          return instructorName;
       }
    
       public String getLocation() {
          return location;
       }
    
       public String getClassTime() {
          return classTime;
       }
    
       // Override printInfo() to include extra details
       @Override
       public void printInfo() {
          // Call base class version to print course number/title
          super.printInfo();
    
          // Print additional OfferedCourse info
          System.out.println("   Instructor Name: " + instructorName);
          System.out.println("   Location: " + location);
          System.out.println("   Class Time: " + classTime);
       }
    }
    // ===== end =====
    
    
    
    import java.util.Scanner;
    
    public class CourseInformation {
       public static void main(String[] args) {
          Scanner scnr = new Scanner(System.in);
    
          // Create base class object
          Course course1 = new Course();
    
          // Create derived class object
          OfferedCourse course2 = new OfferedCourse();
    
          // Read input values
          String course1Num = scnr.nextLine();
          String course1Title = scnr.nextLine();
          String course2Num = scnr.nextLine();
          String course2Title = scnr.nextLine();
          String instructor = scnr.nextLine();
          String location = scnr.nextLine();
          String classTime = scnr.nextLine();
    
          // Set values for base course
          course1.setCourseNumber(course1Num);
          course1.setCourseTitle(course1Title);
    
          // Set values for offered course
          course2.setCourseNumber(course2Num);
          course2.setCourseTitle(course2Title);
          course2.setInstructorName(instructor);
          course2.setLocation(location);
          course2.setClassTime(classTime);
    
          // Print information for both
          course1.printInfo();
          course2.printInfo();
    
          scnr.close();
       }
    }
