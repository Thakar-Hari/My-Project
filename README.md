/*# My-Project
This Project Contains Scientific Calculator , Maze , Matchstick , Tic-Tac-Toe game. The Scientific Calculator here can perform "Matrix Multiplication , Inverse of Matrix and lot more".*/
#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#define SIZE 5
int main()
{
    int choice;
    printf("This program contains :\n\t1. A Scientific Calculator\n\t2. A Matchstick Game\n\t3. A Maze Game\n\t4. A Tic-Tac-Toe Game.\n");
    printf("Enter your choice(1-4) : ");
    scanf("%d", &choice);
    switch (choice)
    {
        case 1:
        {
            printf("You Selected Scientific Calculator.\n");
            int choice1; 
            printf("You have the Following Functions :\n\t1. Matrix Multiplication\n\t2. Inverse of Matrix\n\t3. Triginometric Ratios\n\t4. Logarithm(Natural and Base 10)\n\t5. Addition, Multiplication, Division, Substraction\n\t6. Power of any number raised to any number.\n\t7. Complex Form\n\t8. Exit.\n");
            printf("Enter the value(1-7) : ");
            scanf("%d", &choice1);
            switch (choice1)
            {
                case 1:
                {
                    int r1, c1, r2, c2;    
                    printf("Enter number of rows of first matrix: ");
                    scanf("%d", &r1);
                    printf("Enter number of columns of first matrix (and rows of second matrix): ");
                    scanf("%d", &c1);
                    r2 = c1;
                    printf("Enter number of columns of second matrix: ");
                    scanf("%d", &c2);
                    int mat1[r1][c1], mat2[r2][c2], result[r1][c2];
                    printf("Enter elements of first matrix (%d * %d):\n", r1, c1);
                    for (int i = 0; i < r1; i++) 
                    {
                        for (int j = 0; j < c1; j++) 
                        {
                                scanf("%d", &mat1[i][j]);
                        }
                    }    
                    printf("Enter elements of second matrix (%d * %d):\n", r2, c2);
                    for (int i = 0; i < r2; i++) 
                    {
                        for (int j = 0; j < c2; j++) 
                        {
                            scanf("%d", &mat2[i][j]);
                        }
                    }
                    for (int i = 0; i < r1; i++) {
                        for (int j = 0; j < c2; j++) {
                            result[i][j] = 0;
                        }
                    }
                    for (int i = 0; i < r1; i++)
                    {
                        for (int j = 0; j < c2; j++)
                        {
                            for (int k = 0; k < c1; k++) 
                            {
                                result[i][j] += mat1[i][k] * mat2[k][j];
                            }
                        }
                    }
                    printf("Resultant matrix (%d * %d):\n", r1, c2);
                    for (int i = 0; i < r1; i++) 
                    {
                        for (int j = 0; j < c2; j++) 
                        {
                            printf("%d ", result[i][j]);
                        }
                        printf("\n");
                    }
                    break;
                }
                case 2:
                {
                    
                    int n;
                    printf("Enter the order of the square matrix: ");
                    scanf("%d", &n);
                    float mat[n][2*n];
                    printf("Enter elements of the matrix (%d * %d):\n", n, n);
                    for (int i = 0; i < n; i++) 
                    {
                        for (int j = 0; j < n; j++) 
                        {
                            scanf("%f", &mat[i][j]);
                        }
                    }
                    for (int i = 0; i < n; i++) 
                    {
                        for (int j = n; j < 2*n; j++) 
                        {
                            mat[i][j] = (j == i+n) ? 1 : 0;
                        }
                    }
                    for (int i = 0; i < n; i++) 
                    {
                        float diag = mat[i][i];
                        if (diag == 0) 
                        {
                            printf("Matrix is singular, cannot find inverse.\n");
                            return 0;
                        }
                        for (int j = 0; j < 2*n; j++) 
                        {
                            mat[i][j] /= diag;
                        }
                        for (int k = 0; k < n; k++) 
                        {
                            if (k != i) 
                            {
                                float factor = mat[k][i];
                                for (int j = 0; j < 2*n; j++) 
                                {
                                    mat[k][j] -= factor * mat[i][j];
                                }
                            }
                        }
                    }
                    printf("Inverse matrix:\n");
                    for (int i = 0; i < n; i++) 
                    {
                        for (int j = n; j < 2*n; j++) 
                        {
                            printf("%8.3f ", mat[i][j]);
                        }
                        printf("\n");
                    }
                    break;
                }
                case 3:
                {
                    double a, b, c, d, e, f, g;
                    printf("Enter the value of angle in degrees : ");
                    scanf("%lf", &a);
                    b = (a*3.14)/180.0;
                    printf("Sin(%.2lf) value = %.2lf\n",a, sin(b));
                    printf("Cos(%.2lf) value = %.2lf\n",a, cos(b));
                    printf("Tan(%.2lf) value = %.2lf\n",a, tan(b));
                    printf("Cosecant(%.2lf) value = %.2lf\n",a, (1.0/sin(b)));
                    printf("Secant(%.2lf) value = %.2lf\n",a, (1.0/cos(b)));
                    printf("Cotangent(%.2lf) value = %.2lf\n",a, (1.0/tan(b)));
                    break;
                }  
                case 4:
                {
                    double a, b, c;
                    printf("Enter the number : ");
                    scanf("%lf", &a);
                    b = log(a);
                    c = (log(a))/(2.303);
                    printf("The Natural Logarithm of %.2lf is : %.4lf\n", a, b);
                    printf("The Base 10 Logrithm of %.2lf is : %.4lf\n", a, c);
                    break;
                }
                case 5:
                {
                    int choice, n;
                    double numbers[100], result;
                    printf("Scientific Calculator - Basic Operations\n");
                    printf("Choose an operation:\n");
                    printf("\t1. Addition\n");
                    printf("\t2. Subtraction\n");
                    printf("\t3. Multiplication\n");
                    printf("\t4. Division\n");
                    printf("Enter your choice (1-4): ");
                    scanf("%d", &choice);
                    printf("Enter how many numbers you want to calculate: ");
                    scanf("%d", &n);
                    printf("Enter %d numbers:\n", n);
                    for (int i = 0; i < n; i++) 
                    {
                        scanf("%lf", &numbers[i]);
                    }
                    switch (choice) 
                    {
                        case 1:
                        {
                            result = 0;
                            for (int i = 0; i < n; i++) {
                                result += numbers[i];
                            }
                            printf("Sum = %.4lf\n", result);
                            break;
                        }    
                        case 2:
                        {
                            result = numbers[0];
                            for (int i = 1; i < n; i++) {
                                result -= numbers[i];
                            }
                            printf("Difference = %.4lf\n", result);
                            break;
                        }    
                        case 3:
                        {
                            result = 1;
                            for (int i = 0; i < n; i++) {
                                result *= numbers[i];
                            }
                            printf("Product = %.4lf\n", result);
                            break;
                        }    
                        case 4:
                        {
                            result = numbers[0];
                            for (int i = 1; i < n; i++) {
                                if (numbers[i] == 0) {
                                    printf("Error: Division by zero encountered.\n");
                                    return 0;
                                }
                                result /= numbers[i];
                            }
                            printf("Result after division = %.4lf\n", result);
                            break;
                        }    
                        default:
                            printf("Invalid choice.\n");
                        break;
                    }
                }
                case 6:
                {
                    double a, b, c, d;
                    printf("Enter the value of number which will get the power : ");
                    scanf("%lf", &a);
                    printf("Enter the value of second number which will be raised on the first number : ");
                    scanf("%lf", &b);
                    c = pow(a, b);
                    printf("The value of %.2lf raised to the number %.2lf is : %.4lf", b, a, c);
                    break;
                }
                case 7:
                {
                    double real, imag, r, theta, degree;
                    printf("Enter the real value : ");
                    scanf("%lf", &real);
                    printf("Enter the imaginary part value : ");
                    scanf("%lf", &imag);
                    r = sqrt(real*real + imag*imag);
                    theta = atan2(imag, real);
                    degree = (theta * 180.0)/(3.14);
                    printf("The Modulus r is : %.4lf\n", r);
                    printf("The angle is : %.4lf in radians and %.4lf in degree\n", theta, degree);
                    break;
                }
                case 8:
                {
                    printf("Exiting Scientific Calculator.....\n");
                    return 0;
                }   
                default:
                    printf("Invalid Choice ! Enter the value between 1-8\n");              
            }
        }
        case 2:
        {
                int matchsticks = 21;
                int user_choice, computer_choice;
                printf("\n This is a matchstick game, The rules are as follows : \n (1) There are 21 matchsticks in total.\n (2) You can pick only 1, 2, 3 or 4 matchsticks at a time.\n (3) The player is supposed to pick the matchsticks first.\n (4) The one who picks up the last matchsticks loses the game. \n");
                while (matchsticks > 1)
                {
                    printf("Enter the number of matchsticks you want to pick (1-4) : ");
                    scanf("%d", &user_choice);
                    if (user_choice < 1 || user_choice > 4)
                    {
                        printf("Invalid Choice, Please choose between 1 to 4 matchsticks only. \n");
                        continue;
                    }
                    computer_choice = 5 - user_choice;
                    matchsticks = matchsticks - user_choice - computer_choice;
                    printf("You picked %d matchsticks, Computer picked %d matchsticks, Remaining matchsticks are : %d \n", user_choice, computer_choice, matchsticks);
                }
                printf("(Attention!) Now only one matchstick is left, \n Your turn is to pick it, \n So you have to pick the last matchstick. \n You Lose the game.");
                return 0;
        }
        case 3:
        {
                    printf("--- Welcome to the Maze Game ---\n");
                    printf("Control your player (P) using W (Up), A (Left), S (Down), D (Right).\n");
                    printf("Reach the Exit (E) to win!\n\n");
                    // 1 represents Wall (#), 0 represents Path (' '), E represents Exit, P represents Player
                    // For a 5x5 grid based on your #define SIZE 5
                    char maze[SIZE][SIZE] = {
                        {'P', ' ', '#', '#', '#'},
                        {'#', ' ', ' ', ' ', '#'},
                        {'#', '#', '#', ' ', '#'},
                        {'#', ' ', ' ', ' ', ' '},
                        {'#', '#', '#', '#', 'E'}
                    };
                    // Track Player Coordinates
                    int pRow = 0, pCol = 0; 
                    char move;
                    int won = 0;
                    while (!won) {
                        // Display the Maze
                        printf("\n");
                        for (int i = 0; i < SIZE; i++) {
                            for (int j = 0; j < SIZE; j++) {
                                printf("%c ", maze[i][j]);
                            }
                            printf("\n");
                        }
                        printf("\nEnter move (W/A/S/D) or 'Q' to quit: ");
                        // Note the space before %c to clear any leftover newline characters in the buffer
                        scanf(" %c", &move); 
                        if (move == 'Q' || move == 'q') {
                            printf("Exiting Maze Game.\n");
                            break;
                        }
                        // Calculate Next Target Position
                        int nextRow = pRow;
                        int nextCol = pCol;
                        if (move == 'W' || move == 'w') nextRow--;
                        else if (move == 'S' || move == 's') nextRow++;
                        else if (move == 'A' || move == 'a') nextCol--;
                        else if (move == 'D' || move == 'd') nextCol++;
                        else {
                            printf("Invalid input! Use W, A, S, or D.\n");
                            continue;
                        }
                        // Bound Check: Ensure target is within the 5x5 matrix boundaries
                        if (nextRow >= 0 && nextRow < SIZE && nextCol >= 0 && nextCol < SIZE) 
                        {    
                            // Check if player reached the exit
                            if (maze[nextRow][nextCol] == 'E') {
                                maze[pRow][pCol] = ' '; // Clear old position
                                maze[nextRow][nextCol] = 'P'; // Move to exit
                                
                                // Print final layout
                                for (int i = 0; i < SIZE; i++) {
                                    for (int j = 0; j < SIZE; j++) printf("%c ", maze[i][j]);
                                    printf("\n");
                                }
                                
                                printf("\n Congratulations! You solved the maze!\n");
                                won = 1;
                            }
                            // Check if target space is an open path
                            else if (maze[nextRow][nextCol] == ' ') {
                                maze[pRow][pCol] = ' '; // Clear old space
                                maze[nextRow][nextCol] = 'P'; // Set new space
                                pRow = nextRow;
                                pCol = nextCol;
                            } 
                            else {
                                printf("Ouch! You hit a wall (#).\n");
                            }
                        } else {
                            printf("Movement out of bounds!\n");
                        }
                    }
                    break;
                    }
                case 4:
        {
            printf("--- Welcome to Tic-Tac-Toe! ---\n");
            printf("Player 1 is [X]  |  Player 2 is [O]\n");
            printf("Enter coordinates as (row column) from 1 to 3. Example: 1 2\n\n");

            // Initialize a blank 3x3 game board grid
            char board[3][3] = {
                {' ', ' ', ' '},
                {' ', ' ', ' '},
                {' ', ' ', ' '}
            };

            int player = 1; // 1 for Player X, 2 for Player O
            int totalMoves = 0;
            int gameStatus = 0; // 0 = Ongoing, 1 = Win, 2 = Draw
            char mark;

            while (gameStatus == 0)
            {
                // 1. Render the current visual state of the board
                printf("\n");
                printf("  1   2   3 \n");
                printf("1  %c | %c | %c \n", board[0][0], board[0][1], board[0][2]);
                printf("  ---+---+---\n");
                printf("2  %c | %c | %c \n", board[1][0], board[1][1], board[1][2]);
                printf("  ---+---+---\n");
                printf("3  %c | %c | %c \n", board[2][0], board[2][1], board[2][2]);
                printf("\n");

                // Determine active mark token
                mark = (player == 1) ? 'X' : 'O';
                
                int row, col;
                printf("Player %d (%c), enter row and column (1-3): ", player, mark);
                
                // Read grid placement inputs
                if (scanf("%d %d", &row, &col) != 2) {
                    printf("Invalid numerical input format. Try again.\n");
                    while (getchar() != '\n'); // Purge stream buffer
                    continue;
                }

                // Convert 1-based indexing to 0-based array indices
                row--; 
                col--;

                // 2. Validate move parameters
                if (row < 0 || row >= 3 || col < 0 || col >= 3) 
                {
                    printf("Coordinates out of bounds! Choose integers between 1 and 3.\n");
                    continue;
                }
                if (board[row][col] != ' ') 
                {
                    printf("That cell is already occupied! Try a different spot.\n");
                    continue;
                }

                // Place the token onto the matrix grid
                board[row][col] = mark;
                totalMoves++;

                // 3. Scan for Win Vectors (Rows, Columns, and Diagonals)
                for (int i = 0; i < 3; i++) 
                {
                    // Check rows and columns simultaneously
                    if ((board[i][0] == mark && board[i][1] == mark && board[i][2] == mark) ||
                        (board[0][i] == mark && board[1][i] == mark && board[2][i] == mark)) 
                    {
                        gameStatus = 1;
                    }
                }
                // Check primary and secondary diagonals
                if ((board[0][0] == mark && board[1][1] == mark && board[2][2] == mark) ||
                    (board[0][2] == mark && board[1][1] == mark && board[2][0] == mark)) 
                {
                    gameStatus = 1;
                }

                // Check for a full board without a winner (Draw)
                if (gameStatus == 0 && totalMoves == 9) 
                {
                    gameStatus = 2;
                }

                // Handle state transitions
                if (gameStatus == 1) {
                    // Print the winning board arrangement
                    printf("\nFinal Board Layout:\n");
                    printf("  %c | %c | %c \n ---+---+---\n  %c | %c | %c \n ---+---+---\n  %c | %c | %c \n", 
                           board[0][0], board[0][1], board[0][2], board[1][0], board[1][1], board[1][2], board[2][0], board[2][1], board[2][2]);
                    printf("\n Player %d (%c) wins the match!\n", player, mark);
                } 
                else if (gameStatus == 2) {
                    printf("\nThe game ends in a Draw!\n");
                } 
                else {
                    // Switch active turn toggle between 1 and 2
                    player = (player == 1) ? 2 : 1;
                }
            }
            break;
        }
    }
}
 