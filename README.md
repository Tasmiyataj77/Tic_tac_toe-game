# Tic_tac_toe-game



def print_board(board):
    print("\n")
    print(f" {board[0]} | {board[1]} | {board[2]} ")
    print("---|---|---")
    print(f" {board[3]} | {board[4]} | {board[5]} ")
    print("---|---|---")
    print(f" {board[6]} | {board[7]} | {board[8]} ")
    print("\n")


# Function to check if a player has won
def check_winner(board, player):
    win_conditions = [(0, 1, 2), (3, 4, 5), (6, 7, 8),  # Horizontal
                      (0, 3, 6), (1, 4, 7), (2, 5, 8),  # Vertical
                      (0, 4, 8), (2, 4, 6)]             # Diagonal
    for condition in win_conditions:
        if board[condition[0]] == board[condition[1]] == board[condition[2]] == player:
            return True
    return False


# Function to check if the game is a tie
def check_tie(board):
    return all([spot == 'X' or spot == 'O' for spot in board])


# Function to play the Tic-Tac-Toe game
def play_game():
    board = [' ' for _ in range(9)]  # Initialize an empty board
    current_player = 'X'

    while True:
        print_board(board)

        # Ask the current player for their move
        move = int(input(f"Player {current_player}, enter your move (1-9): ")) - 1

        # Check if the move is valid
        if board[move] != ' ':
            print("Invalid move! Try again.")
            continue

        # Place the player's move on the board
        board[move] = current_player

        # Check if the current player has won
        if check_winner(board, current_player):
            print_board(board)
            print(f"Player {current_player} wins!")
            break

        # Check for a tie
        if check_tie(board):
            print_board(board)
            print("It's a tie!")
            break

        # Switch to the other player
        current_player = 'O' if current_player == 'X' else 'X'


if __name__ == "__main__":
    play_game()
