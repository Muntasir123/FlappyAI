# FlappyAI
A JavaScript Responsive Mobile Version of Flappy Bird

Feel free to download and run the index.html file. 

The "AI" portion of this uses an A* search algorithm. The original idea was to use recursion with the following. First we must
generate a random array based on the position of the current `canvas`.

for example  we can consider the following pseudo code

`Maze = { { '*', ' ', '*', '*', '*', '*', '*', '*', '*' },
               { '*', ' ', ' ', ' ', ' ', ' ', '*', ' ', '*' }, { '*', ' ', '*', '*', '*', '*', '*', ' ', '*' },
               { '*', ' ', '*', ' ', '*', ' ', ' ', ' ', '*' }, { '*', ' ', '*', ' ', '*', '*', '*', ' ', '*' },
               { '*', ' ', ' ', ' ', '*', ' ', ' ', ' ', '*' }, { '*', '*', '*', ' ', '*', ' ', '*', ' ', '*' },
               { '*', ' ', ' ', ' ', ' ', ' ', '*', ' ', '*' }, { '*', '*', '*', '*', '*', '*', '*', ' ', '*' } };`
               
The first idea was to find the path with ' ', to escape the maze. We can do this by starting at a random point and using recursion to 
work our way either right to left, or top to bottom.
 
I tested this out for smaller cases in java by using my own stopwatch class using `getTimeMillis()` method. 

    public class MazeDemo {

     // function to print maze
     public static void printMaze(char[][] Maze, int i, int j) {
         int rows = Maze.length;
         int cols = Maze[0].length;
         if ((i < rows)) {
             if (j < cols) {
                 System.out.print(Maze[i][j]);
                 j++;
                 printMaze(Maze, i, j);
             } else if (j == cols) {
                 i++;
                 j = 0;
                 System.out.println();
                 printMaze(Maze, i, j);
             }
         }
     }

     // function to check whether can escape from maze.
     public static boolean escapeMaze(char[][] Maze, int i, int j, boolean canEscape) {
         int rows = Maze.length;
         int cols = Maze[0].length;
         if (i == rows || j == cols)
             if (canEscape) // can escape
                 return true;
             else
                 return false; // cannot escape
         else if ((i < rows)) {
             if (j < cols) {
                 if (Maze[i][j] == ' ') {
                     canEscape = true;
                     i++;
                     j = 0;
                 } else {
                     canEscape = false;
                     j++;
                 }
             }
         }
         return escapeMaze(Maze, i, j, canEscape);
     }

This method has a pretty bad time complexity ( `O(b^k)`)
To combat all this, I simply used my old Java grade 12 project's algorithm of using an A* search.
