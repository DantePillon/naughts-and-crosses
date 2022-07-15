import java.util.Arrays;
import java.util.InputMismatchException;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {

        //String gridSeq = scan.nextLine();
        char[][] grid = new char[3][3];
        int turnNum = 0;

        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                grid[i][j] = '_';
            }
        }
        while (!isFinished(grid)) {
            printGrid(gridToString(grid));
            if (turnNum == 9) {
                System.out.println("Draw");
                break;
            }
            while (true) {
                if (readCoordinates(grid, turnNum)) break;
            }
            turnNum++;
        }


        // System.out.println(gameState(grid));

    }
    static boolean readCoordinates(char[][] grid, int turnNum) {
        Scanner scan = new Scanner(System.in);
        System.out.println("Enter the coordinates: ");
        try {
            int yIndex = scan.nextInt() - 1;
            int xIndex = scan.nextInt() - 1;

            if (grid[yIndex][xIndex] == '_') {
                if (turnNum % 2 == 0) {
                    grid[yIndex][xIndex] = 'X';
                } else {
                    grid[yIndex][xIndex] = 'O';
                }
                return true;
            } else {
                System.out.println("This cell is occupied! Choose another one!");
                return false;
            }
        } catch (InputMismatchException e) {
            System.out.println("You should enter numbers!");
            return false;
        } catch (IndexOutOfBoundsException e) {
            System.out.println("Coordinates should be from 1 to 3!");
            return false;
        }
    }

    static String gridToString(char[][] grid) {
        StringBuilder result = new StringBuilder();
        for (char[] array : grid) {
            result.append(Arrays.toString(array).replaceAll("[{}\\[\\] ,]", ""));
        } // the RegEx omits the format of toString(); I could have overridden the method but I forgot how.
        return result.toString();
    }

    static void printGrid(String gridSeq) {
        System.out.println("---------");
        for (int i = 0; i < 9;) {
            System.out.printf("| %s %s %s |%n", gridSeq.charAt(i++), gridSeq.charAt(i++), gridSeq.charAt(i++));
        }
        System.out.println("---------");
    }

    static String gameStateV1(char[][] grid) {

        boolean winX = false;
        boolean winO = false;
        int countXInArray = 0;
        int countOInArray = 0;
        int countX = 0;
        int countO = 0;

        for (char[] row : grid) {
            for (char chr : row) {
                if (chr == 'X') {
                    countX++;
                    countXInArray++;
                } else if (chr == 'O') {
                    countO++;
                    countOInArray++;
                }
            }
            if (countXInArray == 3) {
                winX = true;
            } else if (countOInArray == 3) {
                winO = true;
            }
            countXInArray = 0;
            countOInArray = 0;
        }
        for (int j = 0; j < 3; j++) {
            for (char[] chars : grid) {
                if (chars[j] == 'X') {
                    countXInArray++;
                } else if (chars[j] == 'O') {
                    countOInArray++;
                }
            }
            if (countXInArray == 3) {
                winX = true;
            } else if (countOInArray == 3) {
                winO = true;
            }
            countXInArray = 0;
            countOInArray = 0;
        }
        for (int i = 0; i < 3; i++) {
            if (grid[i][i] == 'X') {
                countXInArray++;
            }
            if (grid[i][i] == 'O') {
                countOInArray++;
            }
        }
        if (countXInArray == 3) {
            winX = true;
        } else if (countOInArray == 3) {
            winO = true;
        }
        countXInArray = 0;
        countOInArray = 0;

        for (int i = 0; i < 3; i++) {
            if (grid[i][2 - i] == 'X') {
                countXInArray++;
            }
            if (grid[i][2 - i] == 'O') {
                countOInArray++;
            }
        }
        if (countXInArray == 3) {
            winX = true;
        } else if (countOInArray == 3) {
            winO = true;
        }

        if (Math.abs(countO - countX) > 1 || (winO && winX)) {
            return "Impossible";
        } else if (winX) {
            return "X wins";
        } else if (winO) {
            return "O wins";
        } else if (countO + countX < 9) {
            return "Game not finished";
        } else {
            return "Draw";
        }
    }
    static boolean isFinished (char[][] grid) {
        // This method is like gameState version 2 since O has to go after X
        boolean winX = false;
        boolean winO = false;
        int countXInArray = 0;
        int countOInArray = 0;

        for (char[] row : grid) {
            for (char chr : row) {
                if (chr == 'X') {
                    countXInArray++;
                } else if (chr == 'O') {
                    countOInArray++;
                }
            }
            if (countXInArray == 3) {
                winX = true;
            } else if (countOInArray == 3) {
                winO = true;
            }
            countXInArray = 0;
            countOInArray = 0;
        }
        for (int j = 0; j < 3; j++) {
            for (char[] chars : grid) {
                if (chars[j] == 'X') {
                    countXInArray++;
                } else if (chars[j] == 'O') {
                    countOInArray++;
                }
            }
            if (countXInArray == 3) {
                winX = true;
            } else if (countOInArray == 3) {
                winO = true;
            }
            countXInArray = 0;
            countOInArray = 0;
        }
        for (int i = 0; i < 3; i++) {
            if (grid[i][i] == 'X') {
                countXInArray++;
            }
            if (grid[i][i] == 'O') {
                countOInArray++;
            }
        }
        if (countXInArray == 3) {
            winX = true;
        } else if (countOInArray == 3) {
            winO = true;
        }
        countXInArray = 0;
        countOInArray = 0;

        for (int i = 0; i < 3; i++) {
            if (grid[i][2 - i] == 'X') {
                countXInArray++;
            }
            if (grid[i][2 - i] == 'O') {
                countOInArray++;
            }
        }
        if (countXInArray == 3) {
            winX = true;
        } else if (countOInArray == 3) {
            winO = true;
        }

        if (winX) {
            printGrid(gridToString(grid));
            System.out.println("X wins");
            return true;
        } else if (winO) {
            printGrid(gridToString(grid));
            System.out.println("O wins");
            return true;
        } else {
            return false;
        }
    }
}
