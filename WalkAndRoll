"""
Author: Eliana Wang
Project: Walk and Roll
Concepts Covered: Animated plotting in Matplotlib, probability, expected value
Description: The first part of this project simulates a 2D random walk and plots an animated graph of the walk. The second part of this project simulates rolling a die many times to converge upon the expected value and plots and animated graph of the average of the rolls.
"""

import matplotlib.pyplot as plt

import matplotlib.animation as animation
import numpy as np

"""
Parmaters: none
Return: the positions list (a list of tuples)
Description: this method simulates a 2D random walk by randomly choosing which direction to go for 200 times, and keeping track of the list of positions visited.
"""
def walk():
    x,y = 0,0
    global positions
    positions = [(0,0)]
    
    for i in range(200):
        choice = np.random.choice([1, 2, 3, 4])
        if choice == 1: #left
            x += -1
        elif choice == 2: #right
            x += 1
        elif choice == 3: #up
            y += 1
        elif choice == 4: #down
            y += -1

        positions.append((x,y))

    return positions 

"""
Parmaters: frame
Return: none
Description: this method is used in conjunction with FuncAnimation() from matplotlib to animated the 2D random walk graph. This method is what updates the list of X and Y values each frame.
"""
def animateRandomWalk(frame):
    plt.cla()
    #
    X_vals = [tuple[0] for tuple in positions[:frame+1]] #the list of X values up until this frame
    Y_vals = [tuple[1] for tuple in positions[:frame+1]]

    plt.plot(X_vals, Y_vals)
    plt.xlabel("X")
    plt.ylabel("Y")
    plt.title("Random Walk Simulation")

positions = walk()
fig, ax = plt.subplots()
animation = animation.FuncAnimation(fig, animateRandomWalk, frames=200, interval=30, repeat=False)

plt.show()

"""
Parmaters: none
Return: the averages list (a list of integers)
Description: this method simulates rolling a 6-sided die for 1500 times and keeps track of the running average value.
"""
def roll_die():
    global averages
    averages = [0]

    for i in range(1500):
        roll = np.random.randint(1, 7)
        averages.append((averages[-1]*len(averages) +roll)/ (len(averages) + 1)) #calculating the new value into the average

    return averages

import matplotlib.animation as animation #I have to import this again for some reason

"""
Parmaters: frame
Return: none
Description: this method is used in conjunction with FuncAnimation() from matplotlib to animated the 2D random walk graph. This method is what updates the list of X and Y values each frame.
"""
def animateRoll(frame):
    X_vals.append(frame)
    Y_vals.append(averages[frame])

    plt.cla()

    plt.axhline(y = 3.5, color = 'r', linestyle = '-', label="Expected Value") #3.5 is the expected value
    plt.plot(X_vals, Y_vals, label='Running Average')
    plt.xlabel('Number of Rolls')
    plt.ylabel('Roll Value')
    plt.legend()
    plt.title('Illustration of 6-Sided Die Roll Convergence to Expected Value')

roll_die()

X_vals = []
Y_vals = []
fig, ax = plt.subplots()
animation = animation.FuncAnimation(fig, animateRoll, frames=1500, interval=2, repeat=False)
plt.show()
