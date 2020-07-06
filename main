#0 == blank, 1 == X, 2 == O
board = [
[0, 0, 0],
[0, 0, 0],
[0, 0, 0]
]

value = [0, 1, 2]
value[0] = " "
value[1] = "X"
value[2] = "O"

player = 1
lastX, lastY = -1, -1
won = False

def setup():
    size(600, 600)


def changePlayer():
    global player
    player = player == 1 and 2 or 1

#draw == 0, player1 == 1, player2 == 2
def checkWin(): #x, y is last move x, y
    global won
    
    horizontal = False
    vertical = False
    diagonal = False
    
    
    
    if board[lastY][0] == player and board[lastY][1] == player and board[lastY][2] == player:
        horizontal = True
    
    if board[0][lastX] == player and board[1][lastX] == player and board[2][lastX] == player:
        vertical = True
    
    diagonals = {
    "0,0":True,
    "2,0":True,
    "1,1":True,
    "0,2":True,
    "2,2":True
    }
    
    if diagonals.get(str(lastX) + "," + str(lastY), False) and board[1][1] == player:
        diagonal1 = board[0][0] == player and board[2][2] == player
        diagonal2 = board[2][0] == player and board[0][2] == player
        diagonal = diagonal1 or diagonal2
    
    won = horizontal or vertical or diagonal
    return won


def draw():
    background(85, 85, 85)
    
    w, h = width / 3, height / 3
    
    strokeWeight(14)
    #horizontal lines
    line(0, h, w * 3, h)
    line(0, h * 2, w * 3, h * 2)
    
    #vertical lines
    line(w, 0, w, h * 3)
    line(w * 2, 0, w * 2, h * 3)
    
    for x in range(0, 3):
        for y in range(0, 3):
            xPos = x * w
            yPos = y * h
            
            textSize(160)
            fill(255)
            textAlign(CENTER)
            text(value[board[y][x]], w * x, h * y, w, h)
            


def mousePressed():
    global lastX, lastY
    
    if won:
        return
    
    x = ceil(mouseX / (width * 1.0) * 3) - 1
    y = ceil(mouseY / (height * 1.0) * 3) - 1
    #print(value[board[y][x]])
    
    isZero = board[y][x] == 0
    
    if isZero:
        board[y][x] = player
        lastX, lastY = x, y
        
        print(checkWin())
        
        changePlayer()
     
