#Brooks Tawil
#1/12/2016
#Powerball in Python
#This is a simple python script that simulates the powerball numbers.
#The player inputs their numbers and the selected amount of times the simulation should run.
#Written in VIM

import random

def main():
	print ("This script is used to simulate the powerball winnings. With it you can pick your own whit numbers on a scale from 1-69 with no duplicates. You also choose a single powerball number from 1-26.")
	print ("Finally you can input how many time you would like the simulation to run using your chosen numbers and generation a new set of winning numbers at random. Every run costs $2, the same as a normal powerball ticket.")
	print ("Just note that the odds of winning the jackpot are 1 in 292,201,338. The odds of winning a single prize are 1 in 24.87")
	
	amt_runs = int(input("\nHow many times would you like the simulation to run?(Note: You only have to choose your own numbers once) "))
	total = 0
	player_nums, player_ball = player_input()
	for i in range(amt_runs):
		total += run_single_sim(player_nums,player_ball)
	print("\nYou have run the simulation a total of "+str(amt_runs)+" times.")
	print("You have spent a total of $"+str(amt_runs*2)+" with a revenue of $"+str(amt_runs*2+total)+" and have net winnings of $"+str(total))
	
def player_input():
	#Takes the player input
	i = 0
	player_numbers = [0]*5
	player_ball = 0
	while (i<len(player_numbers)):
		player_numbers[i] = int(input("Input number "+str(i+1)+"(1-69): "))
		
		#If the player chooses a number out of range
		if (player_numbers[i]>69 or player_numbers[i]<1):
			print("Invalid selection, numbers must be between 1 and 69")
			player_numbers[i] = 0
			i -= 1
		
		#If the player chooses a duplicate number
		for j in range(0,i):
			if (player_numbers[j] == player_numbers[i]):
				print("Invalid selection, that number has already been selected")
				player_numbers[i] = 0
				i-=1
		
		i+=1
	for i in range(0,1):
		player_powerball = int(input("Input your powerball(1-26)"))
		
		#If powerball number is out of range
		if (player_powerball>26 or player_powerball<1):
			print("Invalid selection, powerball must be between 1 and 26")
			i-=1
	
	#Comment these lines out to stop the prinouts and signficantly increase the speed 	
	print("Your numbers are: "+str(player_numbers).strip("[]"))
	print("Your powerball is: "+str(player_powerball))
	
	return player_numbers, player_powerball

#Creates random winning numbers and checks against the player's input. Returns total winnings
def run_single_sim(player_numbers, player_powerball):
	winning_numbers = [0]*5
	winning_powerball = random.randint(1,26)
	amt_won = 0
	amt_lost = 0
	net_gain = 0

	
	#Distributes the winning numbers
	i=0
	while (i<len(winning_numbers)):
		winning_numbers[i] = random.randint(1,69)
		for j in range(0,i):
			if (winning_numbers[j] == winning_numbers[i]):
				winning_numbers[i] = 0
				i-=1
		i+=1	 
	print("The numbers are: "+str(winning_numbers).strip("[]")+". The powerball is: "+str(winning_powerball))
	
	#Checks the normal numbers to see how many are matched
	amt_of_matches = 0
	for i in winning_numbers:
		for j in player_numbers:
			if i == j:
				amt_of_matches += 1
		
	#Checks if the player won and if so how much
	#http://www.powerball.com/powerball/pb_prizes.aspprizes 
	prizes = {
		(0, False):0,
		(1, False):0,
		(2, False):0,
		(3, False):7,
		(4, False):100,
		(5, False):1000000,
		(0, True):4,
		(1, True):4,
		(2, True):7,
		(3, True):100,
		(4, True):50000,
		(5, True):1300000000
	}
	is_powerball = (player_powerball == winning_powerball)
	#Look using the keys to find the cash prize value
	matches = (amt_of_matches, is_powerball)
	prize = prizes[matches]
	amt_won = prize
	amt_lost = 2
	net_gain = amt_won - amt_lost
	print("You just won $"+str(amt_won))
	
	return net_gain
	
main()
