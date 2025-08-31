#1. Flowchart: https://drive.google.com/file/d/18duqwv2niMOvGPNFUVRfvQs1ElY19n7T/view?usp=sharing

#2. I chose bubble sorting. I didn't actually know that's what it's called but it's when two elements
nect to each other are compared to each other to dictate a boolean value. I thought this would be the easiest
since we have to evaluate a boolean for the loop into the array. This is also the method I was taught, so it was most familiar to me.

#3. I thought it was a little bit of a challenge trying to understand the instructions. But it was a little hard remembering parseInt and making sure that
there was no comma after the last printed number in the final list. I felt like the bubble swap aspect was just a little difficult since I haven't coded since Spring semester.

#4. Video: https://www.loom.com/share/4634efa926a0457a850db7758e849846

#5: Code
    
    import java.util.Scanner;

    public class Main {

    /*method to sort myArr into desc order*/
    public static void sortArray(int[] myArr, int arrSize) {
        //outer loop: runs (arrSize - 1) times
        for (int i = 0; i < arrSize - 1; i++) {
            //inner loop: checking if left element is less than right element
            for (int j = 0; j < arrSize - 1 - i; j++) {
                // if inner loop true:
                if (myArr[j] < myArr[j + 1]) {
                    // swap elements (bubble swap method)
                    int temp = myArr[j]; //temp = left element
                    myArr[j] = myArr[j + 1]; //move right element to left
                    myArr[j + 1] = temp; //left/temp element to right
                }
            }
        }
    }

    /*main method*/
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // take String list and separate by spaces
        String[] input = sc.nextLine().split(" ");

        // size of array by reading first number
        int arrSize = Integer.parseInt(input[0]); //parseInt since we took in a String value; must convert

        // create array with size of arrSize
        int[] myArr = new int[arrSize];

        // fill array with remaining numbers
        for (int i = 0; i < arrSize; i++) {
            myArr[i] = Integer.parseInt(input[i + 1]); //skip first value since it was the size
        }

        // call method to create descending order
        sortArray(myArr, arrSize);

        /* print sorted array */
        for (int i = 0; i < arrSize; i++) {
            System.out.print(myArr[i]); // printing each element
            if (i < arrSize - 1) {
                System.out.print(","); //prints comma if it is not the last element; nothing after last element
            }
        }
    }
}
