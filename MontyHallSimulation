"""
Name: Eliana Wang
Date: 9/5/2024
Period: 9
Purpose: To run 100 simulations of the Monty Hall problem and visualize whether switching choices or staying is more likely to result in a win.
"""

import random
import matplotlib.pyplot as plt

"""
Name: runOneTime()
Parameters: string stayOrSwitch
Return: string "loss" or "win"
Description: This function runs one simulation of the Monty Hall problem. It randomly assigns the doors to have 1 car and 2 goats. It randomly picks one of the door and either stays with that choice or switches depending on the input. Then, it returns whether the door had a goat (loss) or a car (win).
"""
def runOneTime(stayOrSwitch):
    doors = {1:"", 2:"", 3:""}
    randint = random.randrange(1, 4)

    # Randomly assign one of the choices a “car”, the other two “goats”
    doors[randint] = "car"
    for i in doors:
        if doors[i] != "car":
            doors[i] = "goat"

    # Pick with equal probability one of three choices
    firstChoice = random.randrange(1, 4)

    # Have the “host” reveal an unchosen door containing a goat
    for i in doors:
        if doors[i] == "goat" and i != firstChoice:
            revealed = i

    finalChoice = ""
    if stayOrSwitch == "switch":
        for i in doors:
            if i != firstChoice and i != revealed:
                finalChoice = i
    else:
        finalChoice = firstChoice

    # determine outcome
    if doors[finalChoice] == "goat":
        outcome = "loss"
    else:
        outcome = "win"

    print("The player originally chose Door", str(firstChoice)+". Door", revealed,"was revealed to have a Goat. The player chose to", stayOrSwitch, "to Door", finalChoice, "and the outcome was a", outcome+".")
    return outcome

stayResults = []
stayWins = 0
switchResults = []
switchWins = 0

for i in range(100):
    outcome = runOneTime("stay")
    if outcome == "win":
        stayWins += 1
    stayResults.append(stayWins)

for i in range(100):
    outcome = runOneTime("switch")
    if outcome == "win":
        switchWins += 1
    switchResults.append(switchWins)

trials = [i for i in range(1, 101)]
plt.scatter(trials, stayResults, label="Wins (Staying)", s=1)
plt.scatter(trials, switchResults, label="Wins (Switching)", s=1)
plt.legend()
plt.xlabel("Trials")
plt.ylabel("Wins")
plt.show()
