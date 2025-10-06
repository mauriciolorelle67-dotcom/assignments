## Flowchart: 
https://drive.google.com/file/d/1SpxVzKBkAAo13y7hhJIbXBqv-Pr_0P0d/view?usp=sharing

## Challenges:
I needed to think about the access modifiers because I can't access lastName or ageYears since they're declared private in the Person class.

## Video:


## Code: 
    
    public class StudentDerivationFromPerson {
       public static void main(String[] args) {
          // Create a new Student object called courseStudent
          Student courseStudent = new Student();

      // Set the student's last name to "Smith"
      courseStudent.setName("Smith");

      // Set the student's age to 20
      courseStudent.setAge(20);

      // Set the student's ID number to 9999
      courseStudent.setID(9999);

      // Call the inherited printAll() method from Person class
      // This will print: "Name: Smith, Age: 20"
      courseStudent.printAll();

      // Use a separate println() to print the student's ID
      // This adds ", ID: 9999" to the same line and moves to a new line at the end
      System.out.println(", ID: " + courseStudent.getID());
       }
    }
