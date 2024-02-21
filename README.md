# Connect-Four-Kyu-4
Solution for the Kata Kyu 4 Connect-Four
~~~
import java.util.*;

public class ConnectFour {
    public static String whoIsWinner(List<String> piecesPositionList) {
        int[][] array ={ {0,0,0,0,0,0,0},
                         {0,0,0,0,0,0,0},
                         {0,0,0,0,0,0,0},
                         {0,0,0,0,0,0,0},
                         {0,0,0,0,0,0,0},
                         {0,0,0,0,0,0,0}};

        HashMap<Character, Integer> hm = new HashMap<Character, Integer>();
        hm.put('A', 0);
        hm.put('B', 1);
        hm.put('C', 2);
        hm.put('D', 3);
        hm.put('E', 4);
        hm.put('F', 5);
        hm.put('G', 6);

        String response = "Draw";

        for (int i = 0; i < piecesPositionList.size(); i++) {
            String turn = piecesPositionList.get(i);
            int column = hm.get(turn.charAt(0));
            char player = turn.charAt(2);
          
            array = input(column, player, array);
            response = checkWin(array);
          
            if (!response.equals("Draw")) {
                return response;
            }
        }          
        return response;
    }
    public static int[][] input(int column, char player, int[][] array) {
        for (int i = array.length-1; i >= 0; i--) {
            if (array[i][column] == 0) {
                if (player == 'R') {
                    array[i][column] = 1;
                }else array[i][column] = 2;
                break;
            }
        }
        return array;
    }
    public static String checkWin(int[][] array) {
        // Vertical
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < array[i].length; j++) {
                if ((array[i][j] == 1 && array[i+1][j] == 1 && array[i+2][j] == 1 && array[i+3][j] == 1)) {
                    return "Red";
                } else if ((array[i][j] == 2 && array[i+1][j] == 2 && array[i+2][j] == 2 && array[i+3][j] == 2)) {
                    return "Yellow";
                }
            }
        }
        // Horizontal
        for (int i = 0; i < array.length; i++) {
            for (int j = 0; j < 4; j++) {
                if ((array[i][j] == 1 && array[i][j+1] == 1 && array[i][j+2] == 1 && array[i][j+3] == 1)) {
                    return "Red";
                } else if ((array[i][j] == 2 && array[i][j+1] == 2 && array[i][j+2] == 2 && array[i][j+3] == 2)) {
                    return "Yellow";
                }
            }
        }
        // Diagonal
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 4; j++) {
                if ((array[i][j] == 1 && array[i+1][j+1] == 1 && array[i+2][j+2] == 1 && array[i+3][j+3] == 1)) {
                    return "Red";
                } else if ((array[i][j] == 2 && array[i+1][j+1] == 2 && array[i+2][j+2] == 2 && array[i+3][j+3] == 2)) {
                    return "Yellow";
                }
            }
        }
        // Reverse Diagonal
        for (int i = 0; i < 3; i++) {
            for (int j = 6; j > 2; j--) {
                if ((array[i][j] == 1 && array[i+1][j-1] == 1 && array[i+2][j-2] == 1 && array[i+3][j-3] == 1)) {
                    return "Red";
                } else if ((array[i][j] == 2 && array[i+1][j-1] == 2 && array[i+2][j-2] == 2 && array[i+3][j-3] == 2)) {
                    return "Yellow";
                }
            }
        }
        return "Draw";
    }
}
~~~
