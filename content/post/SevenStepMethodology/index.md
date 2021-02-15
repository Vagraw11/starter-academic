---
title: Solve any Programming Problem using the Seven-Step Methodology
# subtitle: Learning how to use the syntax for a given programming language is one thing and understanding the methodology for problem-solving is another. A programmer friend of mine recently acquainted me with an interesting seven-step approach to translate any problem into a working code to solve it. The seven-step methodology as discussed by Hilton et al. can be utilized to implement the simple yet classic game of tic-tac-toe.
# Summary for listings and search engines
# summary: Learning how to use the syntax for a given programming language is one thing and understanding the methodology for problem-solving is another. A programmer friend of mine recently acquainted me with an interesting seven-step approach to translate any problem into a working code to solve it. The seven-step methodology as discussed by Hilton et al. can be utilized to implement the simple yet classic game of tic-tac-toe.
# Link this post with a project
projects: []

# Date published
date: "2020-12-13T00:00:00Z"

# Date updated
lastmod: "2020-10-05T00:00:00Z"

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
#image:
#  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
#  focal_point: ""
#  placement: 2
#  preview_only: false

authors:
- admin

tags:
- Programming, Problem Solving

categories:
- Intersection

---

##  

**Step 1: Work an Example By Hand**
In our case this meant playing multiple rounds of tic-tac-toe with another player on a piece of paper, to understand what leads to a win or a draw. Two players, X and O, take turns to make their marks in a 3×3 grid. To win the game, a player must place three of their marks in a horizontal, vertical, or diagonal row. The game is over once all the 9 squares are filled.

**Step 2: Write Down What You Did**
This step involves writing exactly what you did while playing the game. For example, marking the position on the 3 x 3 grid that each player placed their mark on until a player wins the game. More precisely, we did the following:
1.	Make a 3x3 grid.
2.	Player ‘O’ or ‘X’ fills in their position of interest, followed by the next player.
3.	Once all the 9 squares are filled, we check if there is a draw or a winner.

**Step 3: Find Patterns and Generalize**
Herein we try identifying repeating segments, conditions and generalize all the possible solutions and corresponding positions in a matrix or an array.
1.	For simplicity, we can assign each position in the 3x3 grid (0 to 8) to a one-dimensional board.
2.	This vector can then be filled with ‘X’s or ‘O’s based on the user choice.
3.	Each time user makes the choice the 1D board can be filled with the user marker (O or X) at the assigned position (a whole number between 0 and 8).
4.	To check for the winner, we can generalize the winning positions from the indices of the grid, namely: {0,1,2}, {3, 4, 5},   {6, 7, 8},   {2, 5, 8},   {0, 3, 6},   {1, 4, 7},   {0, 4, 8}, and  {2, 4, 6}
To summarize, the game starts with player O selecting a position on the grid to place their mark on. The input should be between 0 and 8, inclusive. The 1D board will then be filled with the designated mark for the player, i.e. O or X at the given position. The next player (Player X) will then go through the same steps and then move to the player O again and so on. Once all the 9 positions on the board are filled, the winner will be determined after checking the winning conditions. If none of the winning conditions are met, it will be declared a draw.

**Step 4: Check By Hand**
The step involves checking your algorithm with a different set of inputs i.e. play a new game but this time check the outcomes highlighted in step 3.

**Step 5: Translate to Code**
We used the Python syntax to write the code for the algorithm highlighted in step 3 as shown below:

import sys
class ttt:
    def __init__(self):                                           # Constructor
        self.board = list();                                      # Initialize board array
        for i in range (0,9):
            self.board.append('e')                                # Fill board array with 'e' to signify empty
        self.character_map = {'e': ' ', '0': '0', 'X': 'X'}       # Print blank wherever 'e'
        self.num_turns = 0                                        # Initialize number of turns
        self.players = ('0', 'X')                                 # Fixed array for 'Os and Xs representing players'
        self.player = self.players[0]                             # Initialize Player to be O
        
    def play(self):                                               # Method to play the game: Function inside a class
        welcome_message = ("Hello! This is tic-tac-toe, a two player game"
                            "played between player 0 and player X."
                            "The game is played in a 3 x 3 matrix. Each cell of the matrix has an index from 1-9."
                            "Row one has cells 1, 2 and 3."
                            "Row one has cells 4, 5 and 6."
                            "Row one has cells 7, 8 and 9."
                            "The game starts with player 0 selecting an index followed by player X, followed by player 0 and so on."
                            "The game stops when one of the two players win or when the game is a draw.")
        print(welcome_message)
        self.print_board()
        while True:            
            self.user_choice = self.get_input()                 
            self.fill_array(self.user_choice, self.player)
            self.print_board()
            if self.check_winner(self.player):
                print(f'{self.player} won the game!')
                sys.exit()
                pass
            elif self.board.count('e') == 0:
                print(f"It's a draw!")
                sys.exit()
                pass
            
            if self.num_turns % 2 == 0:
                self.player = self.players[1]
            else:
                self.player = self.players[0]
            self.num_turns += 1
            pass
        pass
    
    # Method 1: User Choice that makes use of valid choice
    # returns true if user_choice is an integer in range [0,8] and 
    # if user_choice hasn't been selected before.
    def valid_choice(self, user_choice):              
        if  user_choice >= 1 and \
            user_choice <= 9 and \
            self.board[user_choice-1] == 'e':
            return True
        return False
    
    def get_input(self):  
        is_valid_choice = False
        while not is_valid_choice:
            try:
                user_choice = int(input(f"Player {self.player}'s turn. Enter a number between 1 and 9 (inclusive) that has not been entered before:"))
                is_valid_choice = self.valid_choice(user_choice)
            except ValueError:
                print("Error! Input should be an integer.")
                is_valid_choice = False
        return user_choice - 1
    
    # Method 2: Fill_array 
    def fill_array(self, user_choice, player):
        self.board[user_choice] = player
        pass
     
    # Method 3: Print_Board
    def print_board(self):
        print("\n")
        print(self.character_map[self.board[0]], '|', self.character_map[self.board[1]], '|', self.character_map[self.board[2]])
        print('-'* 10)
        print(self.character_map[self.board[3]], '|', self.character_map[self.board[4]], '|', self.character_map[self.board[5]])
        print('-'* 10)
        print(self.character_map[self.board[6]], '|', self.character_map[self.board[7]], '|', self.character_map[self.board[8]])
        print("\n")
        pass
    
    # Method 4: Check_Winner
    def check_winner(self, player):
        if  (self.board[0] == self.board[1] == self.board[2] == player) or \
            (self.board[3] == self.board[4] == self.board[5] == player) or \
            (self.board[6] == self.board[7] == self.board[8] == player) or \
            (self.board[0] == self.board[3] == self.board[6] == player) or \
            (self.board[1] == self.board[4] == self.board[7] == player) or \
            (self.board[2] == self.board[5] == self.board[8] == player) or \
            (self.board[0] == self.board[4] == self.board[8] == player) or \
            (self.board[2] == self.board[4] == self.board[6] == player):
            return True
        return False
    pass
    
    if __name__ == "__main__":
    game = ttt()
    game.play()
    pass

**Step 6: Run Test Cases**
Now we execute the program and check the answer, else we debug failed test case.

**Step 7: Debug Failed Test Cases**
If there is a problem in the algorithm, we may return to step 3 and fix it. If it is an implementation issue, we may return to step 5 to fix the code.

**Reference**: Hilton, Andrew D., Genevieve M. Lipp, and Susan H. Rodger. "Translation from Problem to Code in Seven Steps." Proceedings of the ACM Conference on Global Computing Education. 2019.
