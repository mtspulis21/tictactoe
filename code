# STEP 1 - displaying board

def display_board(board):
    print(board[1] + ' | ' + board[2] + ' | ' + board[3])
    print('----------')
    print(board[4] + ' | ' + board[5] + ' | ' + board[6])
    print('----------')
    print(board[7] + ' | ' + board[8] + ' | ' + board[9])
    
# test 1 - board
test_board = [' ']*10
display_board(test_board)

# STEP 2 - creating player marker selection function
def player_input():
    marker = ''
    
    while not (marker == 'X' or marker == 'O'):
        marker = input('Player 1, please pick a marker, ''X'' or ''O'': ').upper()
        
    if marker == 'X':
        return ('X','O')
    else:
        return ('O','X')
        
# STEP 3 - board takes the position and subs with marker from player       
def place_marker(board, marker, position):
  board[position] = marker
  
# test 2 - marker placement
place_marker(test_board,'F',1)
place_marker(test_board,'F',4)
place_marker(test_board,'F',7)
display_board(test_board)

# STEP 4 - creating win conditions
def win_check(board,mark):
    return ((board[7] == mark and board[8] == mark and board[9] == mark) or # across the bottom
    (board[4] == mark and board[5] == mark and board[6] == mark) or # across the middle
    (board[1] == mark and board[2] == mark and board[3] == mark) or # across the top
    (board[7] == mark and board[4] == mark and board[1] == mark) or # down the left side
    (board[8] == mark and board[5] == mark and board[2] == mark) or # down the middle
    (board[9] == mark and board[6] == mark and board[3] == mark) or # down the right side
    (board[7] == mark and board[5] == mark and board[3] == mark) or # diagonal
    (board[9] == mark and board[5] == mark and board[1] == mark)) # diagonal

# STEP 5 - check board spaces if empty or full for win conditions
def space_check(board, position):
    return board[position] == ''
    
def full_board_check(board):
    for i in range(1,10):
        if space_check(board, i):
            return False
    return True
# STEP 6 - player choose where do place marker
def player_choice(board):
    position = 0
    
    while position not in [1,2,3,4,5,6,7,8,9] or not space_check(board,position):
        position = int(input('Choose your next position: (1-9) '))
        
    return position
    
# STEP 7 - replay function
def replay():
    return input('Do you want to play again? Yes or No: ').lower().startswith('y')
    
# STEP 8 - randomize player who starts
import random

def choose_first():
    if random.randint(0,1) == 0:
        return 'Player 2'
    else:
        return 'Player 1'
        
        
# STEP 9 - game logic

print('Welcome to Tic Tac Toe')

while True:
    game_board = ['']*10
    player1_marker, player2_marker = player_input()
    turn = choose_first()
    print(turn + ' will start.')
    
    play_game = input('Are you ready to play? Y or N: ')
    
    if play_game.lower() == 'y':
        game_on = True
    else:
        game_on = False
        
    while game_on:
        if turn == 'Player 1':
            # Player 1 começa
            
            display_board(game_board)
            position = player_choice(game_board)
            place_marker(game_board,player1_marker,position)
            
            if win_check(game_board, player1_marker):
                display_board(game_board)
                print('Player 1 has won the game')
                game_on = False
            else:
                if full_board_check(game_board):
                    display_board(game_board)
                    print('The game has drawn')
                    break
                else:
                    turn = 'Player 2'
                    
        else:
            display_board(game_board)
            position = player_choice(game_board)
            place_marker(game_board,player2_marker,position)
            
            if win_check(game_board, player2_marker):
                display_board(game_board)
                print('Player 2 has won the game')
                game_on = False
            else:
                if full_board_check(game_board):
                    display_board(game_board)
                    print('The game has drawn')
                    break
                else:
                    turn = 'Player 1'
                    
    if not replay():
        break

