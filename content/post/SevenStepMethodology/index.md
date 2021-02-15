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

# Featured image
# Place an image named `im1.jpg/png` in this page's folder and customize its options here.
#image:
#  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
#  focal_point: ""
#  placement: 2
#  preview_only: false

**Step 2: Write Down What You Did**
This step involves writing exactly what you did while playing the game. For example, marking the position on the 3 x 3 grid that each player placed their mark on until a player wins the game. More precisely, we did the following:
1.	Make a 3x3 grid.
2.	Player ‘O’ or ‘X’ fills in their position of interest, followed by the next player.
3.	Once all the 9 squares are filled, we check if there is a draw or a winner.

# Featured image
# Place an image named `im2.jpg/png` in this page's folder and customize its options here.
#image:
#  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/CpkOjOcXdUY)'
#  focal_point: ""
#  placement: 2
#  preview_only: false

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

**Step 6: Run Test Cases**
Now we execute the program and check the answer, else we debug failed test case.

**Step 7: Debug Failed Test Cases**
If there is a problem in the algorithm, we may return to step 3 and fix it. If it is an implementation issue, we may return to step 5 to fix the code.

**Reference**: Hilton, Andrew D., Genevieve M. Lipp, and Susan H. Rodger. "Translation from Problem to Code in Seven Steps." Proceedings of the ACM Conference on Global Computing Education. 2019.
