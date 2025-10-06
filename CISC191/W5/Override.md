## Flowchart:
https://drive.google.com/file/d/1AV4dlDU5SsFYqwwT-N5jCd1HQ5KhLOH-/view?usp=sharing

## Challenges:
I mixed up nextLine() and nextInt() and then I ended up skipping some input.

## Video:


## Code:
    // ===== Code from file Book.java =====
    public class Book {
       // Private fields for book information
       private String title;
       private String author;
       private String publisher;
       private String publicationDate;
    
       // Setter methods for private fields
       public void setTitle(String bookTitle) {
          title = bookTitle;
       }
    
       public void setAuthor(String bookAuthor) {
          author = bookAuthor;
       }
    
       public void setPublisher(String bookPublisher) {
          publisher = bookPublisher;
       }
    
       public void setPublicationDate(String pubDate) {
          publicationDate = pubDate;
       }
    
       // Getter methods
       public String getTitle() {
          return title;
       }
    
       public String getAuthor() {
          return author;
       }
    
       public String getPublisher() {
          return publisher;
       }
    
       public String getPublicationDate() {
          return publicationDate;
       }
    
       // Print basic book information
       public void printInfo() {
          System.out.println("Book Information: ");
          System.out.println("   Book Title: " + title);
          System.out.println("   Author: " + author);
          System.out.println("   Publisher: " + publisher);
          System.out.println("   Publication Date: " + publicationDate);
       }
    }
    // ===== end =====
    
    
    // ===== Code from file Encyclopedia.java =====
    public class Encyclopedia extends Book {
       // Additional fields specific to an encyclopedia
       private String edition;
       private int numPages;
    
       // Setter methods
       public void setEdition(String encyEdition) {
          edition = encyEdition;
       }
    
       public void setNumPages(int pages) {
          numPages = pages;
       }
    
       // Getter methods
       public String getEdition() {
          return edition;
       }
    
       public int getNumPages() {
          return numPages;
       }
    
       // Override printInfo() from Book to include new fields
       @Override
       public void printInfo() {
          // Call the parent class version first
          super.printInfo();
    
          // Then print encyclopedia-specific details
          System.out.println("   Edition: " + edition);
          System.out.println("   Number of Pages: " + numPages);
       }
    }
    // ===== end =====


    // ===== Code from file BookInformation.java =====
    import java.util.Scanner;
    
    public class BookInformation {
       public static void main(String[] args) {
          Scanner scnr = new Scanner(System.in);

      // Create objects
      Book book1 = new Book();
      Encyclopedia encyclopedia1 = new Encyclopedia();

      // Read input for Book object
      String bookTitle = scnr.nextLine();
      String bookAuthor = scnr.nextLine();
      String bookPublisher = scnr.nextLine();
      String bookPubDate = scnr.nextLine();

      // Read input for Encyclopedia object
      String encyTitle = scnr.nextLine();
      String encyAuthor = scnr.nextLine();
      String encyPublisher = scnr.nextLine();
      String encyPubDate = scnr.nextLine();
      String encyEdition = scnr.nextLine();
      int encyPages = scnr.nextInt();

      // Set fields for Book
      book1.setTitle(bookTitle);
      book1.setAuthor(bookAuthor);
      book1.setPublisher(bookPublisher);
      book1.setPublicationDate(bookPubDate);

      // Set fields for Encyclopedia
      encyclopedia1.setTitle(encyTitle);
      encyclopedia1.setAuthor(encyAuthor);
      encyclopedia1.setPublisher(encyPublisher);
      encyclopedia1.setPublicationDate(encyPubDate);
      encyclopedia1.setEdition(encyEdition);
      encyclopedia1.setNumPages(encyPages);

      // Print results
      book1.printInfo();
      encyclopedia1.printInfo();

      scnr.close();
   }
}


