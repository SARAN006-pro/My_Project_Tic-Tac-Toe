# My_Project_Tic-Tac-Toe

Project Title:
Tic Tac Toe Game
Language Used:
Python
Objective:
To implement a simple two-player Tic Tac Toe game using Python, which handles user inputs, displays the board after each move, detects the winner or draw, and offers a restart option.
Project Features:
- 3x3 Tic Tac Toe board
- Two-player input (X and O)
- Turn-based play
- Checks for win (rows, columns, diagonals)
- Checks for draw
- Handles invalid input and occupied cells
- Option to restart the game
# Python Code (tic_tac_toe.py):

board = [[" " for _ in range(3)] for _ in range(3)]

def print_board():
    for row in board:
        print("|".join(row))
        print("-" * 5)

def check_win(player):
    for i in range(3):
        if all([board[i][j] == player for j in range(3)]) or all([board[j][i] == player for j in range(3)]):
            return True
    if all([board[i][i] == player for i in range(3)]) or all([board[i][2 - i] == player for i in range(3)]):
        return True
    return False

def check_draw():
    for row in board:
        if " " in row:
            return False
    return True

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
