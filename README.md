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

To combat all this, I simply used my old Java grade 12 project's algorithm of using an A* search.
