#1. Flowchart: https://drive.google.com/file/d/1B2Tg-stdHhy88JjFKmoqv_PTZJJoLQBx/view?usp=sharing


#2. For a website, I would copy a text block and then split it by spaces (just like I did in the assignment!).
I would then count how many times each word occurs by using a method such as `getWordFrequency`.
It is important for the code not to be case sensitive, as otherwise, it will give an inaccurate 
count of how many times a word is used.


#3. I struggled with my looping index since I ended up putting <= listSize instead of < listSize. 
I gave myself an ArrayIndexOutOfBoundsException.

#4. Video: https://www.loom.com/share/052186476d624ad0b767ac283695f76c?sid=f355338a-1bb3-40ec-b006-5176d05e107c

#5. Code

    import java.util.Scanner;
      
      public class Main {
      
          //method to count how many times a word appears
          public static int getWordFrequency(String[] wordsList, int listSize, String currWord) {
              int count = 0; //create a count to total how many times a word appears
      
              //looking at every word in list
              for (int j = 0; j < listSize; j++) {
                  if (wordsList[j].equalsIgnoreCase(currWord)) { //equalsIgnoreCase to compare word + ignore capitalization
                      count++; //add one for every matched word regardless of capitalization
                  }
              }
              return count; //returning an int value of total count
          }
      
          public static void main(String[] args) {
              Scanner sc = new Scanner(System.in);
      
              String line = sc.nextLine();//prompt String line for command line
              String[] wordsList = line.split(" "); //split by spaces to get an array of words
              int listSize = wordsList.length;//number of words in the array
      
              //loop to get each word + its frequency
              for (int i = 0; i < listSize; i++) {
                  String currWord = wordsList[i];// current word
                  int count = getWordFrequency(wordsList, listSize, currWord);// count matches
                  System.out.println(currWord + " " + count);// output
              }
          }
}
