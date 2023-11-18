    import java.util.Scanner;
    
    class Performance {
        private int[] marks;
        int[] mark = new int[10];
        int n, mode;
        int[] repetitions = new int[10];
        int count;

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
        int[] frequency = new int[10];
        int k = 0, samples[] = new int[10];
        for (int i = 0; i < 10; i++) samples[i] = marks[i];

        for (int i = 0; i <= 9; i++)
            for (int j = i + 1; j <= 9; j++)
                if (samples[i] == samples[j] && samples[i] != -1) {
                    repetitions[k] = samples[i];
                    frequency[k]++;
                    samples[j] = -1;
                }

        int maxFrequency = frequency[0], modeIndex = 0;
        for (int i = 0; i < 10; i++)
            if (frequency[i] > maxFrequency) {
                maxFrequency = frequency[i];
                modeIndex = i;
            }

        if (maxFrequency == 0) return -1;
        mode = repetitions[modeIndex];
        return mode;
    }

    int getFreqAtMode() {
        int k = 0;
        if (mode == -1) mode = getMode();
        if (mode == -1) return -1;
        else {
            for (int i = 0; i < 10; i++)
                if (mode == marks[i]) k++;
            return k;
        }
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
