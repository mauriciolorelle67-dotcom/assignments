## Flowchart:
https://drive.google.com/file/d/15DT55mXPppg9mzXuTrskWqcc6VUpUy5r/view?usp=sharing
## Challenges:
I had some trouble conceptually understanding this. It was a lot of trial and error looking at some smaller and set int arrays in order to find out how everything works.
## Video:
https://www.loom.com/share/a4d38fa5a96e4756990419b47b0b3a3d
## Code:
    import java.util.Scanner;  //import scanner for input reading
    
    public class InsertionSort {
        public static void main(String[] args) {
            Scanner scan = new Scanner(System.in);  //create scanner to read input
  
            int n = scan.nextInt();//read array size
    
            int[] arr = new int[n]; //create array size 'n'
    
            for (int i = 0; i < n; i++) {//read 'n' ints and store in the array

                arr[i] = scan.nextInt();
            }
  
            printArray(arr); //print the original unsorted array
    
            int comparisons = 0;//initialize counters for comparisons and swaps

            int swaps = 0;
    
            // PERFORMING INSERTION SORT
            for (int i = 1; i < n; i++) { //outer loop starts from second element (index 1)

                int key = arr[i];//the element we want to insert into the sorted part
                int j = i - 1;//index of the last element in the sorted portion
    
                //compare key with elements in the sorted part of the array
                //move elements one position to the right until correct position is found
                while (j >= 0 && arr[j] > key) {
                    comparisons++; //count each comparison
                    arr[j + 1] = arr[j]; //shift the larger element to the right
                    swaps++; //count as a swap (movement)
                    j--; //move left to check the next element
                }
    
                //if we exit loop without failing j >= 0, 
                //then one more comparison occurred
                if (j >= 0) {
                    comparisons++;
                }
              
                arr[j + 1] = key; //place key in its correct sorted position
                
                printArray(arr); //print array after each pass

            }
    
            System.out.println();//print blank line for formatting

            System.out.println("comparisons: " + comparisons); //print total number of comparisons 

            System.out.println("swaps: " + swaps); //print total number of swaps
        }
    
        private static void printArray(int[] arr) { //helper method to print all elements of an array in one line

            for (int num : arr) {
                System.out.print(num + " ");  //print each element followed by a space
            }
            System.out.println();  //move to the next line after printing array
        }
    }
    
