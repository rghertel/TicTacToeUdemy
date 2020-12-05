# TicTacToeUdemy
My first Udemy Milestone Project

from IPython.display import clear_output

def display_board(board):
    #You can clear_output() here
    print('   |   |   ')
    print(f' {board[7]} | {board[8]} | {board[9]} ')
    print('   |   |   ')
    print('-----------')
    print('   |   |   ')
    print(f' {board[4]} | {board[5]} | {board[6]} ')
    print('   |   |   ')
    print('-----------')
    print('   |   |   ')
    print(f' {board[1]} | {board[2]} | {board[3]} ')
    print('   |   |   ')

def player_input():
 
    choice = ''
        
    while choice != 'X' and choice != 'O':
       
        choice = input('Player 1, would you like to be X or O?')
        print(f"Sorry, {choice} isn't an option, please try again")
        
    clear_output()
    
    if choice == 'X':
        print(f'Great, Player 1 is X and Player 2 is O')
        return ('X','O')
    elif choice == 'O':
        print(f'Great, Player 1 is O and Player 2 is X')
        return ('O','X') 
        
def place_marker(board, marker, position):
    
    board[position] = marker

def win_check(board, mark):
    
    return ((board[1]==board[2]==board[3]==mark)or
    (board[4]==board[5]==board[6]==mark)or
    (board[7]==board[8]==board[9]==mark)or
    (board[1]==board[4]==board[7]==mark)or
    (board[2]==board[5]==board[8]==mark)or
    (board[3]==board[6]==board[9]==mark)or
    (board[1]==board[5]==board[9]==mark)or
    (board[3]==board[5]==board[7]==mark))

import random

def choose_first():
    turn = random.choice(['Player 1','Player 2'])
    return(f'{turn} goes first')

def space_check(board, position):
    return board[position] != 'X' and board[position] !='O'
#the space doesnt have an x or an o, so it returns True, or that the space is
#empty

def full_board_check(board):
    for space in range(1,10):
        if space_check(board, space):
            return False
        
    return True

def player_choice(board):

    board_spot = 0
    
    while board_spot != space_check(board, board_spot):
        
        board_spot = int(input(f'Where would you like to place your marker(1-9)?'))
    
    clear_output()
        
    return board_spot
        
        
    #how to check if not integer??
    #if board_spot != list(range(1,10)):
        #print(f"That spot isn't available")
        
def replay():
    play_again = ''
    while play_again != 'Y' and play_again != 'N':
        play_again = input(f'Would you like to play again? (Y or N): ')
        print("Sorry, I didn't understand your answer.")
    
    clear_output()
              
    if play_again == 'Y':
        return True
    
    elif play_again == 'N':Y
        return False
        
        

print('Welcome to Tic Tac Toe!')


while True:
    the_board = [' ']*10
    player_1,player_2 = player_input()
    
    turn = choose_first()
    
    play_game = input('Ready to play? (Y or N):')
    
    if play_game == 'Y':
        game_on = True
    elif play_game == 'N':
        game_on = False
    #DO YOU NEED PLAY_GAME? HOW TO PROGRAM STARTING AUTOMATICALLY?    
    while game_on:
        
        if turn == 'Player 1':
            
            display_board(the_board)
            print(f"{player_1}'s turn")
            mark = player_choice(the_board)
            place_marker(the_board, player_1, mark)
            
            
            if win_check(the_board, player_1):
                display_board(the_board)
                print (f'{turn} wins!')
                game_on = False
            
            elif full_board_check(the_board):
                display_board(the_board)
                print (f"It's a tie!")
                game_on = False
            
            else:
                turn = 'Player 2'
                clear_output()    
                    
        else:
            display_board(the_board)
            print(f"{player_2}'s turn")
            mark = player_choice(the_board)
            place_marker(the_board, player_2, mark)
            
            
            if win_check(the_board, player_2):
                display_board(the_board)
                print (f'{turn} wins!')
                game_on = False
            
            elif full_board_check(the_board):
                display_board(the_board)
                print (f"It's a tie!")
                game_on = False
            
            else:
                turn = 'Player 1'
                clear_output()

    if not replay():
        break
