# Dice Ladder Problem(Probability)
It is Dice Ladder Game Where we will calculate Probability 

Here if you throw a dice and if it is [1,2] then take a onestep down
IF there is 3,4,5 then you go up by 1 step
if it is six then you will throw the dice again and result is the number of steps 
step Can't be negative

![image](https://user-images.githubusercontent.com/77065085/182663006-2bec3de0-03dc-4de9-9124-3abe339ce59e.png)

# Initialize all_walks 
all_walks = []
# Simulate random walk 100 times

for i in range(100) :
    random_walk = [0]
    for x in range(100) :
        step = random_walk[-1]
        dice = np.random.randint(1,7)
        if dice <= 2:
            step = max(0, step - 1)
        elif dice <= 5:
            step = step + 1
        else:
            step = step + np.random.randint(1,7)

        # Implement clumsiness
        if np.random.rand()<=0.001 :
            step = 0

        random_walk.append(step)
    
    # Append random_walk to all_walks
    all_walks.append(random_walk)
# Convert all_walks to NumPy array: np_aw

np_aw=np.array(all_walks)
# Plot np_aw and show
plt.plot(np_aw)
plt.show()
![image](https://user-images.githubusercontent.com/77065085/182663174-507bf423-dd75-4c23-9e84-89400045b60a.png)


# Clear the figure
plt.clf()

# Transpose np_aw: np_aw_t
np_aw_t=np.transpose(np_aw)

# Plot np_aw_t and show
plt.plot(np_aw_t)
plt.show()
![image](https://user-images.githubusercontent.com/77065085/182663210-238fb77b-f5f9-46a6-8496-eddbd8bbc9e0.png)


# Create and plot np_aw_t
np_aw_t = np.transpose(np.array(all_walks))

# Select last row from np_aw_t: ends
ends = np_aw_t[-1,:]

# Plot histogram of ends, display plot
plt.hist(ends)
plt.show()
![image](https://user-images.githubusercontent.com/77065085/182663258-60a564fe-2c83-4c48-b397-7a964ad62f11.png)

#Well then, what's the estimated chance that you'll reach at least 50 steps high if you play this Empire State Building game?
np.mean(ends >= 50)
0.89
#To match the theoretical value we have to run this code trillions of times 
