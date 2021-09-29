import java.util.Scanner;

public class Cinema {
    final static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        System.out.println("Enter the number of rows:");
        int rows = scanner.nextInt();
        System.out.println("Enter the number of seats in each row:");
        int seats = scanner.nextInt();
        int[][] array = new int[rows + 1][seats + 1];
        hallPlan(array);
        action(array, rows, seats);
    }

    public static void action(int[][] array, int rows, int seats) {
        System.out.println();
        System.out.println("1. Show the seats");
        System.out.println("2. Buy a ticket");
        System.out.println("3. Statistics");
        System.out.println("0. Exit");
        int button = scanner.nextInt();
        while (button != 0) {
            if (button == 1) {
                printHall(array, rows, seats);
            } else if (button == 2) {
                chooseSeats(array, rows, seats);
            } else if (button == 3) {
                statistics(array, rows, seats);
            } else {
                continue;
            }
            System.out.println();
            System.out.println("1. Show the seats");
            System.out.println("2. Buy a ticket");
            System.out.println("3. Statistics");
            System.out.println("0. Exit");
            button = scanner.nextInt();
        }

    }
    public static int[][] hallPlan(int array[][]) {
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                if (i == 0 && j == 0){
                    array[i][j] = -1;
                } else {
                    if (i == 0) {
                        array[i][j] = j;
                    } else if (j == 0) {
                        array[i][0] = i;
                    } else {
                        array[i][j] = 0;
                    }
                }
            }
        }
        return array;
    }

    public static void printHall(int array[][], int rows, int seats) {
        System.out.println();
        System.out.println("Cinema:");
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                if (array[i][j] == 0) {
                   if (j < 10) {
                       System.out.print("S" + " ");
                   } else {
                       System.out.print("S" + "  ");
                   }
                } else if (array[i][j] == -2) {
                    if (j < 10) {
                        System.out.print("B" + " ");
                    } else {
                        System.out.print("B" + "  ");
                    }
                } else if (array[i][j] == -1) {
                    System.out.print("   ");
                } else {
                    if (i < 10 && j == 0) {
                        System.out.print(array[i][j] + "  ");
                    } else {
                        System.out.print(array[i][j] + " ");
                    }
                }
            }
            System.out.println();
        }
    }

    public static int[][] chooseSeats(int[][] array, int rows, int seats) {
        System.out.println();
        System.out.println("Enter a row number:");
        int row = scanner.nextInt();
        System.out.println("Enter a seat number in that row:");
        int seat = scanner.nextInt();
        System.out.println();
        if (row <= 0 || row > rows || seat <= 0 || seat > seats) {
            System.out.println("Wrong input!");
            chooseSeats(array, rows, seats);
        } else if (array[row][seat] == -2) {
            System.out.println("That ticket has already been purchased!");
            chooseSeats(array, rows, seats);
        } else if (rows * seats < 60) {
            System.out.println("Ticket price: $10");
        } else {
            if (rows / 2 >= row) {
                System.out.println("Ticket price: $10");
            } else {
                System.out.println("Ticket price: $8");
            }
        }
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                if (i == row && j == seat) {
                    array[i][j] = -2;
                }
            }
        }
        return array;
    }

    public static void statistics(int[][] array, int rows, int seats) {
        int total = 0;
        int current = 0;
        char c = '%';
        float percentage = 0;
        int ticketsSmallHall = 0;
        int ticketsFirstPart = 0;
        int ticketsSecondPart = 0;
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < array[i].length; j++) {
                if (rows * seats < 60 && array[i][j] == -2) {
                    ticketsSmallHall++;
                } else if (i <= rows / 2 && array[i][j] == -2){
                    ticketsFirstPart++;
                } else if ( i > rows / 2 && array[i][j] == -2){
                    ticketsSecondPart++;
                }
            }
        }
        System.out.println();
        if (rows * seats < 60) {
            total = rows * seats * 10;
            current = ticketsSmallHall * 10;
            System.out.println("Number of purchased tickets: " + ticketsSmallHall);
        } else {
            total = rows / 2 * seats * 10 + (rows - rows / 2) * seats * 8;
            current = ticketsFirstPart * 10 + ticketsSecondPart * 8;
            System.out.println("Number of purchased tickets: " + (ticketsFirstPart + ticketsSecondPart));
        }
        if (ticketsSmallHall != 0) {
            percentage = (float) 100 / (rows * seats) * ticketsSmallHall;
            System.out.printf("Percentage: %.2f%c%n", percentage, c);
        } else {
            percentage = (float) 100 / (rows * seats) * (ticketsFirstPart + ticketsSecondPart);
            System.out.printf("Percentage: %.2f%c%n", percentage, c);
        }
        System.out.println("Current income: $" + current);
        System.out.println("Total income: $" + total);
    }
}
