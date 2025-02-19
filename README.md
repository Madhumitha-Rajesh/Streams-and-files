# Streams-and-files

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.List;
import java.util.stream.Collectors;

public class StreamAndFileExample {
    public static void main(String[] args) {
        // Define file paths
        String inputFilePath = "input_numbers.txt";
        String outputFilePath = "output_squares.txt";

        try {
            // Read numbers from the input file using BufferedReader and Java streams
            List<Integer> numbers = readNumbersFromFile(inputFilePath);

            // Calculate squares using Java streams
            List<Integer> squares = numbers.stream()
                    .map(num -> num * num)
                    .collect(Collectors.toList());

            // Write squares to the output file using BufferedWriter
            writeSquaresToFile(outputFilePath, squares);

            System.out.println("Squares written to " + outputFilePath);

        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    // Read numbers from a file using BufferedReader and Java streams
    private static List<Integer> readNumbersFromFile(String filePath) throws IOException {
        try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {
            return reader.lines()
                    .map(Integer::parseInt)
                    .collect(Collectors.toList());
        }
    }

    // Write squares to a file using BufferedWriter
    private static void writeSquaresToFile(String filePath, List<Integer> squares) throws IOException {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(filePath))) {
            for (Integer square : squares) {
                writer.write(square.toString());
                writer.newLine();
            }
        }
    }
}

Output-

1
4
9
16
25
