## 1. Flowchart:
https://drive.google.com/file/d/1YcfwEizMumYf5bZRbpVlj5pviOToOCzo/view?usp=sharing

## 2. Challenges: 
I was having trouble designing this around using try-catch, so my program was crashing on invalid input.

## 3. Video:
https://www.loom.com/share/247ee980e6104690b07455ede6f862ba?sid=937fae0c-c96a-4db9-a926-e7b0c8f06768

## 4. Code: 
    import java.util.Scanner; //imports Scanner for user input
    
    public class Pedometer { //class definition
    
        //method that converts steps to miles
        public static double stepsToMiles(int steps) throws Exception {
            // Check for invalid (negative) input
            if (steps < 0) {
                //throw an exception if steps are negative
                throw new Exception("Exception: Negative step count entered.");
            }
            //convert steps to miles (2000 steps = 1 mile)
            return steps / 2000.0;
        }
    
        public static void main(String[] args) {
            Scanner scnr = new Scanner(System.in); //create a Scanner for input
            int steps = scnr.nextInt();            //read integer input from user
            
            try {
                //try to convert steps to miles
                double miles = stepsToMiles(steps);
    
                //print result with 2 decimal places
                System.out.printf("%.2f", miles);
            } catch (Exception e) {
                //if exception occurs, print the custom message
                System.out.println(e.getMessage());
            }
        }
    }
