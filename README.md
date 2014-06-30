Python_examples
===============

All small scripts I created while learning python

---------------------------------------------------
#Game to select where battleship is hidden
    from random import randint
    
    board = []
    
    for x in range(5):
        board.append(["O"] * 5)
    
    def print_board(board):
        for row in board:
            print " ".join(row)
    
    print "Let's play Battleship!"
    print_board(board)
    
    def random_row(board):
        return randint(0, len(board) - 1)
    
    def random_col(board):
        return randint(0, len(board[0]) - 1)
    
    ship_row = random_row(board)
    ship_col = random_col(board)
    
    turn = 0
    for i in range(4):    
        turn = turn + 1
        print "Turn", turn
        guess_row = int(raw_input("Guess Row:"))
        guess_col = int(raw_input("Guess Col:"))
        
        if guess_row == ship_row and guess_col == ship_col:
            print "Congratulations! You sunk my battleship!"
            break
        else:
            if (guess_row < 0 or guess_row > 4) or (guess_col < 0 or guess_col > 4):
                print "Oops, that's not even in the ocean."
            elif(board[guess_row][guess_col] == "X"):
                print "You guessed that one already."
            else:
                print "You missed my battleship!"
                board[guess_row][guess_col] = "X"
            
                print_board(board)
            if(turn == 4):
                print "Game Over"
    
-----------------------------------------------------------
#get string reverse
    def reverse(text):
    count = len(text) -1
    reverse = ""
    while(count>=0):
        reverse = reverse +text[count]
        count -=1
    return reverse    
    
    reverse("abcd!")
------------------------------------------------------------
# Prints anti-vowels from the input string
    def anti_vowel(text):
        count = len(text) - 1
        final = ""
        for i in text:
            if i not in "aeiouAEIOU":
                final = final + i
        return final            
                    
    anti_vowel("Hello World")
-------------------------------------------------------------
#Get Scrabble score
    score = {"a": 1, "c": 3, "b": 3, "e": 1, "d": 2, "g": 2, 
             "f": 4, "i": 1, "h": 4, "k": 5, "j": 8, "m": 3, 
             "l": 1, "o": 1, "n": 1, "q": 10, "p": 3, "s": 1, 
             "r": 1, "u": 1, "t": 1, "w": 4, "v": 4, "y": 4, 
             "x": 8, "z": 10}
    
    def scrabble_score(word):
        word = word.lower()
        count = 0
        for i in word:
            count = count + score[i]
        return count
        
    scrabble_score("pie")
