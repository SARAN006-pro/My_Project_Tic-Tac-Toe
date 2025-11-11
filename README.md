Tic Tac Toe Game (Python Project)
Project Overview

This project is a simple command-line based Tic Tac Toe game developed in Python, designed for two players. The game follows traditional Tic Tac Toe rules, offering a clear interface, turn-based play, and automatic detection of win or draw conditions. The program also includes basic input validation and allows restarting the game.

Objective

To implement a user-friendly two-player Tic Tac Toe game that:

Accepts valid player moves

Displays the updated board after each turn

Detects winning conditions and draw states

Ensures smooth and interactive gameplay experience

Features
Feature	Description
3x3 Board Display	The board is printed clearly after each move.
Two-Player Mode	Players take turns using symbols X and O.
Win Detection	Automatically checks rows, columns, and diagonals.
Draw Detection	Declares a draw when the board is full.
Input Validation	Handles invalid coordinates and occupied cells.
Simple and Interactive	Easy to run and understand.
How the Game Works

The game starts with Player X.

Each player inputs a move in the form:
row,column (Example: 2,3)

The board updates after every move.

The game checks:

If the player has won

Or if the game ends in a draw

The game ends and announces the result.

Program Structure
Function	Purpose
print_board()	Displays the current Tic Tac Toe board.
check_win(player)	Checks if the given player has a winning pattern.
check_draw()	Determines if the game is a draw.
play_game()	Controls the main game loop and player turns.
Source Code
board = [[" " for _ in range(3)] for _ in range(3)]

def print_board():
    for row in board:
        print("|".join(row))
        print("-" * 5)

def check_win(player):
    for i in range(3):
        if all([board[i][j] == player for j in range(3)]) or any([board[j][i] == player for j in range(3)]):
            return True
    if all([board[i][i] == player for i in range(3)]) or all([board[i][2-i] == player for i in range(3)]):
        return True
    return False

def check_draw():
    return all(" " not in row for row in board)

def play_game():
    player = "X"
    while True:
        print_board()
        try:
            move = input(f"Player {player}, enter row and column (1-3): ")
            row, col = map(int, move.split(","))
            row -= 1
            col -= 1

            if row not in range(3) or col not in range(3):
                print("Invalid input! Use numbers 1 to 3.")
                continue

            if board[row][col] != " ":
                print("Position already taken!")
                continue

            board[row][col] = player

            if check_win(player):
                print_board()
                print(f"Player {player} wins!")
                break

            if check_draw():
                print_board()
                print("It's a draw!")
                break

            player = "O" if player == "X" else "X"
        except:
            print("Invalid format! Use row,col like 1,2")

play_game()

Start of Game
<img width="327" height="161" alt="image" src="https://github.com/user-attachments/assets/88760313-6f2c-4d68-b88c-4d6f0fa93d44" />

Player Move	Result Screen
<img width="343" height="126" alt="image" src="https://github.com/user-attachments/assets/4591d14a-7ba5-4057-942e-2844b3eff27f" />

Final Result 
     If Player wins
<img width="343" height="151" alt="image" src="https://github.com/user-attachments/assets/a06cd66a-5ddb-4341-9699-195a3397c8bc" />
    If Game tie
<img width="340" height="146" alt="image" src="https://github.com/user-attachments/assets/bbfb5a98-7257-4753-b4f3-a0f307ca5090" />


Requirements

Python 3.x

Works in any Python environment (IDLE, VS Code, Terminal, etc.)

How to Run
python tic_tac_toe.py

Conclusion

This project demonstrates fundamental Python programming concepts, including:

Lists and loops

Conditional statements

User input handling

Game logic implementation

It is a great beginner-level project to understand logic-building and interactive console applications.
