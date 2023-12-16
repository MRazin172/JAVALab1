    import java.util.Scanner;
    class Performance {
        private int[] marks;

    public Performance() {
        marks = new int[10];

    }
    public void readMarks() {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter the marks for 10 students:");

            for (int i = 0; i < 10; i++) {
                boolean markValid = false;
// here we are checking the validity of the mark, mark should not be greater than 100 or lesser than 0
                       
                    while (!markValid) {
                    System.out.print("Student " + (i + 1) + ": ");
                    int enteredMark = scanner.nextInt();

                    if (enteredMark <= 100 && enteredMark >= 0) {
                        marks[i] = enteredMark;
                        markValid = true;
                    } else {
                        System.out.println("Mark should not be greater than 100 or lesser than 0. Please enter again.");
                    }
                }
            }
        }


    int highestMark() {
        int highest_mark = marks[0];
        for (int mark : marks) {
            if (mark > highest_mark) {
                highest_mark = mark;
            }
        }
        return highest_mark;
    }
    int leastMark() {
        int least = marks[0];
        for (int mark : marks) {
            if (mark < least) {
                least = mark;
            }
        }
        return least;
    }

    int getMode() {
        int mode = -1;
        int maxFrequency = 0;

        for (int i = 0; i < marks.length; i++) {
            int currentMark = marks[i];
            int frequency = 0;

            for (int j = 0; j < marks.length; j++) {
                if (marks[j] == currentMark) {
                    frequency++;
                }
            }

            if (frequency > maxFrequency) {
                maxFrequency = frequency;
                mode = currentMark;
            }
        }

        return mode;
    }


    int getFreqAtMode() {
        int mode = getMode();
        int frequency=0;

        for (int l = 0; l < marks.length; l++) {
            if (marks[l] == mode) {
                frequency++;
            }
        }

        return frequency;
    }
    public void display() {
        System.out.println("Highest Mark: " + highestMark());
        System.out.println("Least Mark: " + leastMark());
        System.out.println("Mode: " + getMode());
        System.out.println("Mode Frequency: " + getFreqAtMode());
    }
    }
    
    public class Main {
        public static void main(String[] args) {
            Performance performance = new Performance();
            performance.readMarks();
            performance.display();
        }
    }
