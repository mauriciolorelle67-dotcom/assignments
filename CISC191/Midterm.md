# MIDTERM QUESTIONS

# VERSION 1
        
        import java.util.*; //SCANNER IMPORT
        
        // PARENT CLASS
        abstract class Item {
            protected String name;       //common to all items
            protected String company;    //common to all items
        
            //constructor
            public Item(String name, String company) {
                this.name = name;
                this.company = company;
            }
        
            //method overloading to set names
            public void setName(String name) {
                this.name = name;
            }
        
            public void setName(String part1, String part2) {
                this.name = part1 + " " + part2;
            }
        
            //abstract methods; override later
            public abstract void update();
            public abstract void display();
        }
        
        // DERIVE CLASS #1: PAINKILLERS
        class Painkiller extends Item {
            private String expiryDate;   // Using String instead of LocalDate
            private String ageGroup;
        
            public Painkiller(String name, String company, String expiryDate, String ageGroup) {
                super(name, company);
                this.expiryDate = expiryDate;
                this.ageGroup = ageGroup;
            }
        
            @Override
            public void update() {
                System.out.println("Updating Painkiller: " + name);
            }
        
            @Override
            public void display() {
                System.out.println("Painkiller -> " + name + " | " + company +
                        " | Expiry: " + expiryDate + " | Age group: " + ageGroup);
            }
        }
        
        //DERIVE CLASS #2: BANDAGE		
        class Bandage extends Item {
            private String expiryDate;
            private String ageGroup;
            private boolean waterproof;
        
            public Bandage(String name, String company, String expiryDate, String ageGroup, boolean waterproof) {
                super(name, company);
                this.expiryDate = expiryDate;
                this.ageGroup = ageGroup;
                this.waterproof = waterproof;
            }
        
            @Override
            public void update() {
                System.out.println("Updating Bandage: " + name);
            }
        
            @Override
            public void display() {
                System.out.println("Bandage -> " + name + " | " + company +
                        " | Expiry: " + expiryDate + " | Age: " + ageGroup +
                        " | Waterproof: " + (waterproof ? "Yes" : "No"));
            }
        }
        
        //DERIVE CLASS #3: EQUIPMENT
        class Equipment extends Item {
            private double weightLbs;
        
            public Equipment(String name, String company, double weightLbs) {
                super(name, company);
                this.weightLbs = weightLbs;
            }
        
            @Override
            public void update() {
                System.out.println("Updating Equipment: " + name);
            }
        
            @Override
            public void display() {
                System.out.println("Equipment -> " + name + " | " + company +
                        " | Weight: " + weightLbs + " lbs");
            }
        }
        
        //MAIN CLASS	
        public class InventoryV1 {
            public static void main(String[] args) {
                Painkiller p = new Painkiller("Motrin", "Amgen", "2023-10-16", "Adult");
                Bandage b = new Bandage("Fabric Bandage", "Johnson & Johnson", "2027-03-10", "All", true);
                Equipment e = new Equipment("Blood Pressure Cuff", "Pfizer", 3.8);
        
                p.display();
                b.display();
                e.display();
            }
        }

# VERSION 2:

    import java.util.*;
    
    public class InventoryV2 {
        public static void main(String[] args) {
            Scanner sc = new Scanner(System.in);
    
            try {
                //painkiller input
                System.out.print("Enter Painkiller Name: ");
                String name = sc.nextLine();
    
                System.out.print("Enter Drug Company: ");
                String company = sc.nextLine();
    
                System.out.print("Enter Expiry Date (e.g. 2025-12-30): ");
                String expiry = sc.nextLine(); // now just a String
    
                System.out.print("Enter Age Group: ");
                String age = sc.nextLine();
    
                Painkiller pk = new Painkiller(name, company, expiry, age);
                pk.display();
    
                //equipment input; catch NumberFormatException
                System.out.print("Enter Equipment Name: ");
                String eqName = sc.nextLine();
    
                System.out.print("Enter Company: ");
                String eqCompany = sc.nextLine();
    
                System.out.print("Enter Weight (lbs): ");
                double weight = Double.parseDouble(sc.nextLine()); 
    //can throw NumberFormatException
    
                Equipment eq = new Equipment(eqName, eqCompany, weight);
                eq.display();
    
            } catch (NumberFormatException e) { //built-in exception #1
                System.out.println("Error: Please enter a valid number for weight.");
            } catch (InputMismatchException e) { //built-in exception #2
                System.out.println("Error: Input type mismatch.");
            } catch (Exception e) { //general fallback
                System.out.println("Unexpected error: " + e.getMessage());
            }
        }
    }

# VERSION 3

    import java.util.*;
    
    // custom exception for invalid age group
    class InvalidAgeGroupException extends Exception {
        public InvalidAgeGroupException(String message) {
            super(message);
        }
    }
    
    // derived Painkiller class throws custom exception
    class PainkillerV3 extends Item {
        private String expiryDate;
        private String ageGroup;
    
        public PainkillerV3(String name, String company, String expiryDate, String ageGroup)
                throws InvalidAgeGroupException {
            super(name, company);
            this.expiryDate = expiryDate;
            setAgeGroup(ageGroup);
        }
    
        public void setAgeGroup(String ageGroup) throws InvalidAgeGroupException {
            //allow only certain options to be valid
            if (!(ageGroup.equalsIgnoreCase("Adult") ||
                  ageGroup.equalsIgnoreCase("Child") ||
                  ageGroup.equalsIgnoreCase("All"))) {
                throw new InvalidAgeGroupException("Invalid Age Group! Must be 'Adult', 'Child', or 'All'.");
            }
            this.ageGroup = ageGroup;
        }
    
        @Override
        public void update() {
            System.out.println("Updating PainkillerV3: " + name);
        }
    
        @Override
        public void display() {
            System.out.println("PainkillerV3 -> " + name + " | " + company +
                    " | Expiry: " + expiryDate + " | Age Group: " + ageGroup);
        }
    }
    
    //MAIN CLASS
    public class InventoryV3 {
        public static void main(String[] args) {
            try {
                // Example of triggering the custom exception
                PainkillerV3 pk = new PainkillerV3("Vicodin", "Sanofi", "2028-10-30", "Teen");
                pk.display();
    
            } catch (InvalidAgeGroupException e) {
                System.out.println("Caught Custom Exception: " + e.getMessage());
            }
        }
      }
