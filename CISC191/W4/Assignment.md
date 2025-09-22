## 1. Flowchart
https://drive.google.com/file/d/1ayn8El_pDFYOkV7eRKvTsotkh4MWYIR7/view?usp=sharing
## 2. Challeges
  I needed to make sure that I knew how to handle "File not Found errors" since a FileNotFoundException will be thrown.
  To do this, I did catch() and printed an error message for the user to let them know their file was invalid.

  ## 3. Video
https://www.loom.com/share/d3be7356f77143c78ebb034997111be4?sid=36bb512d-9d3b-463c-85e9-f3cfc4573b79
  ## 4. Code

      // Import classes for working with files and reading text
    import java.io.File;
    import java.io.FileNotFoundException;
    import java.util.Scanner;
    
    public class PhotoInfoConverter {
        public static void main(String[] args) {
            // Name of the input file that contains the list of photo file names
            String inputFileName = "ParkPhotos.txt";

        try {
            // Create a File object that points to the input text file
            File inputFile = new File(inputFileName);

            // Create a Scanner object to read the contents of the file line by line
            Scanner scanner = new Scanner(inputFile);

            // Loop through the file until there are no more lines
            while (scanner.hasNextLine()) {
                // Read the next line from the file and remove leading/trailing spaces
                String photoFileName = scanner.nextLine().trim();

                // Skip empty lines (just in case there are any)
                if (!photoFileName.isEmpty()) {
                    // Replace the "_photo.jpg" portion with "_info.txt"
                    String infoFileName = photoFileName.replace("_photo.jpg", "_info.txt");

                    // Print the modified file name to the output (console)
                    System.out.println(infoFileName);
                }
            }

            // Close the Scanner to free system resources
            scanner.close();
        } catch (FileNotFoundException e) {
            // If the file is not found, print an error message
            System.out.println("Error: File not found -> " + inputFileName);
        }
    }
    }
