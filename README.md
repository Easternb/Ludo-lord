# Ludo-lord
Stay high on ludo
import random

# Initialize the Ludo board

board = [

    ['-' for _ in range(11)] for _ in range(11)

]

board[0][5] = 'R'

board[5][10] = 'G'

board[10][5] = 'Y'

board[5][0] = 'B'

# Define player colors

colors = {'R': 'Red', 'G': 'Green', 'Y': 'Yellow', 'B': 'Blue'}

# Initialize player positions

player_positions = {'R': [0, 5], 'G': [5, 10], 'Y': [10, 5], 'B': [5, 0]}

# Function to print the board

def print_board():

    for row in board:

        for col in row:

            print(col, end=' ')

        print()

# Function to roll a dice

def roll_dice():

    return random.randint(1, 6)

# Function to move a player

def move_player(color, steps):

    current_row, current_col = player_positions[color]

    board[current_row][current_col] = '-'

    if color == 'R':

        if current_row - steps >= 0:

            current_row -= steps

    elif color == 'G':

        if current_col + steps <= 10:

            current_col += steps

    elif color == 'Y':

        if current_row + steps <= 10:

            current_row += steps

    elif color == 'B':

        if current_col - steps >= 0:

            current_col -= steps

    player_positions[color] = [current_row, current_col]

    board[current_row][current_col] = color

# Main game loop

while True:

    # Print the board

    print_board()

    # Get user input for the player to move

    player_color = input("Enter player color to move (R/G/Y/B): ")

    if player_color not in colors:

        print("Invalid player color!")

        continue

    # Roll the dice

    dice_roll = roll_dice()

    print("Dice roll:", dice_roll)

    # Move the player

    move_player(player_color, dice_roll)

    # Check for a win

    if player_positions[player_color] == [5, 5]:

        print(colors[player_color], "wins!")

        break

        
