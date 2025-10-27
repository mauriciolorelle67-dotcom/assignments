## 1. Flowchart:
https://drive.google.com/file/d/1jNFRwL-FKaBgZfbBePRLTJyvR6hoaD88/view?usp=sharing

## 2. Challenges: 
I was struggling with my loop because I initially used == with char objects instead of comparing primitive char. 

## 3. Video:
https://www.loom.com/share/fec5f9e629104b618c455944d7c2f5fc

## 4. Code: 
        import java.util.Deque;        // Import Deque interface (double-ended queue)
        import java.util.LinkedList;   // Import LinkedList class to use as a Deque
        import java.util.Scanner;      // Import Scanner for user input
        
        public class PalindromeChecker {
            public static void main(String[] args) {
        
                // Create a Scanner object to read input from the user
                Scanner sc = new Scanner(System.in);
        
                // Prompt user to enter a string
                System.out.print("Enter text: ");
        
                // Read the input line and store it in a variable 'input'
                String input = sc.nextLine();
        
                // Convert input to lowercase to ignore case sensitivity
                // Remove all non-alphabetic characters (punctuation, spaces, numbers)
                input = input.toLowerCase().replaceAll("[^a-z]", "");
        
                // Close the scanner to prevent resource leaks
                sc.close();
        
                // Create a Deque (double-ended queue) to hold characters of the input
                Deque<Character> deque = new LinkedList<>();
        
                // Add each character of the input string to the deque (from left to right)
                for (char c : input.toCharArray()) {
                    deque.addLast(c);   // addLast() puts the character at the end
                }
        
                // Assume the string is a palindrome until proven otherwise
                boolean isPalindrome = true;
        
                // Keep checking until there's 1 or 0 characters left in the deque
                while (deque.size() > 1) {
                    // Remove and get the first and last characters
                    char first = deque.removeFirst();   // removes from front
                    char last = deque.removeLast();     // removes from back
        
                    // Compare the characters; if they don't match, it's not a palindrome
                    if (first != last) {
                        isPalindrome = false;           // mark as false
                        break;                          // exit the loop early
                    }
                }
        
                // Display the result based on the flag 'isPalindrome'
                if (isPalindrome) {
                    // If all character pairs matched
                    System.out.println("Yes, " + input + " is a palindrome.");
                } else {
                    // If any mismatch was found
                    System.out.println("No, \"" + input + "\" is not a palindrome.");
                }
            }
        }
