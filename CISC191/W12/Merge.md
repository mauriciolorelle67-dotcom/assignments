## Flowchart:
https://drive.google.com/file/d/1Bms7KNrGUIam-GGwxLYiJj7UHxUkk6VL/view?usp=sharing

## Challenges:
I forgot that the condition of if(left < right) can cause infinite recursion, so I needed to stop the condition. This is why I have the base condition. 

## Video:
https://www.loom.com/share/e8cc2cff7cb54409a6ced2654b6ba942

## Code:
    import java.util.Scanner;
    
    public class MergeSort {
        static int comparisons = 0; //global variable to count comparisons
    
        public static void main(String[] args) {
            Scanner scan = new Scanner(System.in);
    
            int n = scan.nextInt(); //read the size of array

            int[] arr = new int[n]; //create an array and read its elements

            for (int i = 0; i < n; i++) {
                arr[i] = scan.nextInt();
            }
    
            System.out.print("unsorted: "); //print the unsorted array (and label haha)

            printArray(arr);
  
            mergeSort(arr, 0, n - 1); //call mergeSort to sort the array
    
            System.out.print("\nsorted: "); //print the sorted array

            printArray(arr);
    
            System.out.println("\ncomparisons: " + comparisons); //print total comparisons

        }
    
        // Recursive merge sort function
        public static void mergeSort(int[] arr, int left, int right) {
            //base case of only one element
            if (left < right) {
                int mid = (left + right) / 2; //halfway point between starting and ending index
    
                mergeSort(arr, left, mid); //sorting left half
                
                mergeSort(arr, mid + 1, right); //sorting right half

                merge(arr, left, mid, right); //merge the two halves

            }
        }
    
        //function to merge the two halves together
        public static void merge(int[] arr, int left, int mid, int right) {
            int n1 = mid - left + 1; //find sizes of the two subarrays (1)
            int n2 = right - mid; // (2)
    
            int[] L = new int[n1]; //create temp arrays (1)
            int[] R = new int[n2]; //(2)
    
            for (int i = 0; i < n1; i++) //copy data to temp arrays
                L[i] = arr[left + i];
            for (int j = 0; j < n2; j++)
                R[j] = arr[mid + 1 + j];
    
            int i = 0, j = 0, k = left; //merging temp arrays back into arr
    
            while (i < n1 && j < n2) { //compare and merge
                comparisons++; //count every comparison
                if (L[i] <= R[j]) {
                    arr[k] = L[i];
                    i++;
                } else {
                    arr[k] = R[j];
                    j++;
                }
                k++;
            }
    
            while (i < n1) {  //copy remaining elements of L[] (left)
                arr[k] = L[i];
                i++;
                k++;
            }
    
            while (j < n2) { //copy remaining elements of R[] (right)
                arr[k] = R[j];
                j++;
                k++;
            }
        }
    
        //helper method for printing an array
        public static void printArray(int[] arr) {
            for (int i = 0; i < arr.length; i++) {
                System.out.print(arr[i]);
                if (i < arr.length - 1) System.out.print(" ");
            }
            System.out.println();
        }
    }
