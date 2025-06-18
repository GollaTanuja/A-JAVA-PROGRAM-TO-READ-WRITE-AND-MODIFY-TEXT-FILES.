# A-JAVA-PROGRAM-TO-READ-WRITE-AND-MODIFY-TEXT-FILES.
 A SCRIPT DEMONSTRATING FILE OPERATIONS
 import java.io.*;
import java.util.*;

public class FileOperations {

    // Method to write to a file
    public static void writeFile(String filename, String content) {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filename))) {
            writer.write(content);
            System.out.println("File written successfully.");
        } catch (IOException e) {
            System.out.println("Error writing to file: " + e.getMessage());
        }
    }

    // Method to read from a file
    public static void readFile(String filename) {
        try (BufferedReader reader = new BufferedReader(new FileReader(filename))) {
            String line;
            System.out.println("File content:");
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
    }

    // Method to modify a file (example: replace a word)
    public static void modifyFile(String filename, String oldWord, String newWord) {
        File file = new File(filename);
        StringBuilder content = new StringBuilder();

        // Read and modify content
        try (BufferedReader reader = new BufferedReader(new FileReader(file))) {
            String line;
            while ((line = reader.readLine()) != null) {
                content.append(line.replaceAll(oldWord, newWord)).append("\n");
            }
        } catch (IOException e) {
            System.out.println("Error reading file for modification: " + e.getMessage());
            return;
        }

        // Write modified content back
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(file))) {
            writer.write(content.toString());
            System.out.println("File modified successfully.");
        } catch (IOException e) {
            System.out.println("Error writing modified content: " + e.getMessage());
        }
    }

    public static void main(String[] args) {
        String filename = "example.txt";
        String content = "Hello World!\nJava is awesome.\nLet's modify this file.";

        // 1. Write to file
        writeFile(filename, content);

        // 2. Read the file
        readFile(filename);

        // 3. Modify the file
        modifyFile(filename, "Java", "Python");

        // 4. Read again to see changes
        readFile(filename);
    }
}

 
