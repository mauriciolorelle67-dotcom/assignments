#1. Flowchart: https://drive.google.com/file/d/1ksnUE5csA3Rh9JEsH2su9Ee7pzCHmtHY/view?usp=sharing

#2. The thing I was having the most trouble with was understanding the instructions and understanding that there were two ways to do this assignment, not just using one way. 
With the actual code, I was a little confused between the method/constructor parameters (newSearch, newValue) with the fields (search, value) inside the class.
However, I made a clear distinction between the two in my code by using `this.search` and `this.value` in order to tell Java that I'm referring to the class' field and not the local parameter.

#3. Video:

#4. Code:


```
 public class TaxTableTools {

        /** This class searches the 'search' table with a search argument and
         returns the corresponding value in the 'value' table. Variable
         'nEntries' has the number of entries in each table.
         */

        private int [] search =   {   0,  20000, 50000, 100000, Integer.MAX_VALUE };
        private double [] value = { 0.0,   0.10,  0.20,   0.30,              0.40 };
        private int nEntries;

        // ***********************************************************************

        // Default constructor
        public TaxTableTools () {
            nEntries  = search.length; //counting entries for loop boundaries
        }

        // ***********************************************************************

        // TASK A: Setter method to allow updating salary and tax rate tables
        public void setTables(int[] newSearch, double[] newValue) { //called any time after object already exists

            // replacing existing arrays with ones we passed in
            this.search = newSearch; //take the given array and store it inside object's search field
            this.value = newValue; //array of tax rates
            // Update the count of entries so loops still work
            this.nEntries = newSearch.length;
        }

        // TASK B: Overloaded constructor: load *external* tables (born with custom tables)
        public TaxTableTools(int[] newSearch, double[] newValue) { //called when object is created; set up from beginning
            // Assign the caller-provided tables
            this.search = newSearch;
            this.value  = newValue;
            //need to set nEntries to amount of entries to make sure they match and for the loop to work
            this.nEntries = newSearch.length;
        }
        // ***********************************************************************

        // Method to find the tax rate for a given salary
        public double getValue(int searchArgument) {
            double result;        // Will hold the tax rate found
            boolean keepLooking;  // Flag to control the loop
            int i;                // Index for scanning the tables

            result = 0.0;         // Default result (in case not found)
            keepLooking = true;   // Start searching
            i = 0;                // Start from beginning of search table

            // ***********************************************************************

            while ((i < nEntries) && keepLooking) {//loop until we either run out of entries OR find a match
                if (searchArgument <= search[i]) { //if salary is less than or equal to this threshold, assign tax rate for this bracket
                    result = value[i];
                    keepLooking = false;   //stop searching since we found the bracket
                }
                else {
                    ++i; //move to next bracket
                }
            }

            return result;//return the found tax bracket
        }
    }`

```


````
import java.util.Scanner;
//TASK B MAIN
public class IncomeTaxMain {

    // Method to prompt for and input an integer
    public static int getInteger(Scanner input, String prompt) {
        int inputValue;

        System.out.println(prompt + ": ");
        inputValue = input.nextInt();

        return inputValue;
    }

    // ***********************************************************************

    public static void main(String [] args) {
        final String PROMPT_SALARY = "\nEnter annual salary (-1 to exit)";
        Scanner scnr = new Scanner(System.in);
        int annualSalary;
        double taxRate;
        int taxToPay;


        // 2(a) Modify the salary and tax tables in the main method to use
        // different salary ranges and tax rates.
        int []    salaryRange  = {   0,  30000,  60000,  Integer.MAX_VALUE };
        double [] taxRates     = { 0.0,  0.25,   0.35,               0.45 };

        // Access the related class
        // TaxTableTools table = new TaxTableTools();

        // 2(b)Use the just-created overloaded constructor to initialize
        // the salary and tax tables.
        TaxTableTools table = new TaxTableTools(salaryRange, taxRates);

        // Get the first annual salary to process
        annualSalary = getInteger(scnr, PROMPT_SALARY);

        while (annualSalary >= 0) {
            taxRate = table.getValue(annualSalary);
            taxToPay= (int)(annualSalary * taxRate);     // Truncate tax to an integer amount
            System.out.println("Annual Salary: " + annualSalary +
                    "\tTax rate: " + taxRate +
                    "\tTax to pay: " + taxToPay);

            // Get the next annual salary
            annualSalary = getInteger(scnr, PROMPT_SALARY);
        }
    }
} 
`````

```````
import java.util.Scanner;
public class incometax {
//TASK A MAIN
    // Method to prompt for and input an integer
    public static int getInteger(Scanner input, String prompt) {
        int inputValue;

        System.out.println(prompt + ": ");
        inputValue = input.nextInt();

        return inputValue;
    }

    // ***********************************************************************

    public static void main(String [] args) {
        final String PROMPT_SALARY = "\nEnter annual salary (-1 to exit)";
        Scanner scnr = new Scanner(System.in);
        int annualSalary;
        double taxRate;
        int taxToPay;

        // Salary thresholds and tax rates
        int []    salary   = {   0,  20000, 50000, 100000, Integer.MAX_VALUE };
        double [] taxTable = { 0.0,   0.10,  0.20,   0.30,              0.40 };

        // Access the related class
        TaxTableTools table = new TaxTableTools();


        table.setTables(salary, taxTable);//call the setter to load the salary/tax rate tables


        // Get the first annual salary to process
        annualSalary = getInteger(scnr, PROMPT_SALARY);

        while (annualSalary >= 0) {
            taxRate = table.getValue(annualSalary);
            taxToPay= (int)(annualSalary * taxRate);     // Truncate tax to an integer amount
            System.out.println("Annual Salary: " + annualSalary +
                    "\tTax rate: " + taxRate +
                    "\tTax to pay: " + taxToPay);

            // Get the next annual salary
            annualSalary = getInteger(scnr, PROMPT_SALARY);
        }
    }
}

