#This is the game of tic tac toe.

import string
count = 1

board = []
checklist = []

for i in range(0,9):
   board.append("-")

def printboard():
    print("      |   |")
    print("    " + board[0] + " | " + board[1] + " | " + board[2])
    
    print("  ----+---+----")

    print("    " + board[3] + " | " + board[4] + " | " + board[5])
    
    print("  ----+---+----")

    print("    " + board[6] + " | " + board[7] + " | " + board[8])
    print("      |   |")
    print("\n")
printboard()

def check(pos):
    pos -= 1
 #The following is applicable if a player enters 'x' or 'o' in either position 1
    if pos is 0:
        if (board[pos]==board[pos+1] and board[pos]==board[pos+2]):
            return True
            
        elif (board[pos]==board[pos+3] and board[pos]==board[pos+6]):
            return True
        
        elif (board[pos]==board[pos+4] and board[pos]==board[pos+8]):
            return True
        else:
            return False
    
 #The following is applicable if a player enters 'x' or 'o' in either position 2
    elif pos is 1:
        if (board[pos]==board[pos-1] and board[pos]==board[pos+1]):
            return True
            
        elif (board[pos]==board[pos+3] and board[pos]==board[pos+6]):
            return True
        else:
            return False

 #The following is applicable if a player enters 'x' or 'o' in either position 3
    elif pos is 2:
        if (board[pos]==board[pos-1] and board[pos]==board[pos-2]):
            return True
            
        elif (board[pos]==board[pos+3] and board[pos]==board[pos+6]):
            return True
        
        elif (board[pos]==board[pos+2] and board[pos]==board[pos+4]):
            return True
        else:
            return False
 
 #The following is applicable if a player enters 'x' or 'o' in either position 4
    elif pos is 3:
        if (board[pos]==board[pos+1] and board[pos]==board[pos+2]):
            return True
            
        elif (board[pos]==board[pos-3] and board[pos]==board[pos+3]):
            return True
        else:
            return False

 #The following is applicable if a player enters 'x' or 'o' in either position 5
    elif pos is 4:
        if (board[pos]==board[pos-1] and board[pos]==board[pos+1]):
            return True
            
        elif (board[pos]==board[pos+3] and board[pos]==board[pos-3]):
            return True
        
        elif (board[pos]==board[pos+4] and board[pos]==board[pos-4]):
            return True
            
        elif (board[pos]==board[pos+2] and board[pos]==board[pos-2]):
            return True
    
        else:
            return False

 #The following is applicable if a player enters 'x' or 'o' in either position 6
    elif pos is 5:
        if (board[pos]==board[pos-1] and board[pos]==board[pos-2]):
            return True
        elif (board[pos]==board[pos+3] and board[pos]==board[pos-3]):
            return True
        else:
            return False
            
 #The following is applicable if a player enters 'x' or 'o' in either position 7
    elif pos is 6:
        if (board[pos]==board[pos+1] and board[pos]==board[pos+2]):
            return True
            
        elif (board[pos]==board[pos-3] and board[pos]==board[pos-6]):
            return True
        
        elif (board[pos]==board[pos-2] and board[pos]==board[pos-4]):
            return True
        else:
            return False
                                    
 #The following is applicable if a player enters 'x' or 'o' in either position 8
    elif pos is 7:
        if (board[pos]==board[pos-1] and board[pos]==board[pos+1]):
            return True
        elif (board[pos]==board[pos-3] and board[pos]==board[pos-6]):
            return True
        else:
            return False    
                        
 #The following is applicable if a player enters 'x' or 'o' in either position 9
    elif pos is 8:
        if (board[pos]==board[pos-1] and board[pos]==board[pos-2]):
            return True
            
        elif (board[pos]==board[pos-3] and board[pos]==board[pos-6]):
            return True
        
        elif (board[pos]==board[pos-4] and board[pos]==board[pos-8]):
            return True
        else:
            return False

def check_list(var):
    for n in checklist:
        if var==n:
            print("\nCannot enter at pos: " + str(var) + "! Re enter your desired position!\n")
            return True

a = 'x'
b = 'o'

y = True

p1 = input("Enter Player 1: ")
p2 = input("Enter Player 2: ")
print("\n")


while count is not 10:
    if count%2 is 0:
        var = int(input(p2 + ": "))
        
        checkbool = check_list(var)
        
        if checkbool is not True:
            checklist.append(var)
            board[var-1] = b
        
            printboard()
            count += 1
        
            y = check(var)
            if y is True:
                print(p2 + " WINS!")
                exit()
        
        
    elif count%2 is not 0:
        var = int(input(p1 + ": "))
         
        checkbool = check_list(var)
        
        if checkbool is not True:
            checklist.append(var)
            board[var-1] = a
        
            printboard()
            count += 1
        
            y = check(var)
            if y is True:
                print(p1 + " WINS!")
                exit()
            
print("GAME DRAW!!")            
