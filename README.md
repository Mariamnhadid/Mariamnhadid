- 👋 Hi, I’m @Mariamnhadid
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Mariamnhadid/Mariamnhadid is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->#created this using the the time module and the time.sleep() function:
# python3 adventure_game2.py
import random
import time

# Define the maze as a string
maze = """
11111
10001
10101
10000
11111
"""

# Split the maze string into rows
maze_rows = maze.strip().split('\n')

# Get the dimensions of the maze
num_rows = len(maze_rows)
num_cols = len(maze_rows[0])

# Find the starting position and exit position
start_pos = (1, 1)
exit_pos = (num_rows - 2, num_cols - 2)

# Set the player's starting position
player_pos = start_pos

# Define the player movement functions
def move_up(pos):
    row, col = pos
    if maze_rows[row-1][col] == '0':
        return (row-1, col)
    else:
        return pos

def move_down(pos):
    row, col = pos
    if maze_rows[row+1][col] == '0':
        return (row+1, col)
    else:
        return pos

def move_left(pos):
    row, col = pos
    if maze_rows[row][col-1] == '0':
        return (row, col-1)
    else:
        return pos

def move_right(pos):
    row, col = pos
    if maze_rows[row][col+1] == '0':
        return (row, col+1)
    else:
        return pos

# Define the function to print the maze
def print_maze():
    for row in maze_rows:
        print(row)

# Define the function to get the player's move
def get_move():
    move = input("Enter a move (up/down/left/right): ")
    while move not in ['up', 'down', 'left', 'right']:
        move = input("Invalid move. Enter a valid move (up/down/left/right): ")
    return move

# Define the function to generate a random event
def generate_event():
    events = ['You find a treasure chest!', 'You encounter a monster!', 'You discover a hidden passage!']
    return random.choice(events)

# Define the function to handle a random event
def handle_event():
    event = generate_event()
    print(event)
    time.sleep(1)
    if event == 'You find a treasure chest!':
        print("You open the chest and find a bag of gold.")
        return 10
    elif event == 'You encounter a monster!':
        print("The monster attacks you.")
        return -10
    elif event == 'You discover a hidden passage!':
        print("You explore the passage and find a shortcut.")
        return 5

# Set up the game loop
game_over = False
total_score = 0
print("Welcome to the Maze Game!")
time.sleep(1)
print("You need to navigate through the maze to reach the exit.")
time.sleep(1)
print("Enter 'up', 'down', 'left', or 'right' to move in that direction.")
time.sleep(1)
print("You will receive 10 points for each move you make.")
time.sleep(1)
print("Good luck!")
time.sleep(1)

while not game_over:
    # Print the maze
    print_maze()

    # Get the player's move
    move = get_move()

    # Move the player based on the input
    if move == 'up':
        player_pos = move_up(player_pos)
    elif move == 'down':
        player_pos = move_down(player_pos)
    elif move == 'left':
        player_pos = move_left(player_pos)
    elif move == 'right':
        player_pos = move_right(player_pos)

    # Check if the player has reached the exit
    if player_pos == exit_pos:
        game_over = True
        print("Congratulations, you made it to the exit!")
        print("Your final score is:", total_score)
    else:
        # Update the score and print it
        total_score += 10
        print("Your current score is:", total_score)

        # Handle a random event
        if random.randint(1, 10) == 1:
            event_score = handle_event()
            total_score += event_score
            print("Your score is now:", total_score)

