# Particle Swarm Optimization
Minimizing/Maximizing the value of a function.

Long story short: There are `n` particles moving in the domain of the target function. Each particle has a position and a velocity vector. The velocity of
each particle changes in regards to the point where the "best" value of the function was found globaly (among every particle), the point where the "best" value of the
function was meet by this particle, and inertia and a randomness. Each of these parameters has a constant multiplier too.

Here, I've tried to find the minimum of the below cost function:


<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130359662-f19c6aea-e12b-41b0-88db-90404dd35358.png" width="600" />
</p>

<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130360378-91128b7d-dbc3-406f-9d9a-050cbeff0cc4.png" width="200" />
  <img src="https://user-images.githubusercontent.com/12760574/130360386-4a50a435-52b0-4883-a4ab-0390732d2e85.png" width="200" /> 
  <img src="https://user-images.githubusercontent.com/12760574/130360388-be1eaf9a-df31-4e40-800c-3022bfaf6270.png" width="200" />
</p>

### Input:
Single integer `n`, indicating the size of the chess table.

### Process:
Using Genetic/Memetic Algorithm, it finds one way of placing `n` chess queens in the `n*n` table in a way that no two queens threaten each other.

Here, we'll generate some ways of placing the queens in the table. Of course many of them will threaten each other; So the goal is to minimize this cost function.

Here, every genome (answer) is stored as a permutation of numbers `1` to `n`: The `i`-th number represents the number of the column of the queen in `i`-th row. (Note that, no two queens can be in a same row or the same column.) So this code is pretty similar to the code I've written for TSP, [here](https://github.com/ShayanGilmour/TSP-Genetic-Algorithm).

Function `crossover` inputs 2 permutations, and randomly returns one crossover (child) of those two permutations.

Function `cost` inputs one permutation (which represents an answer, ) then returns the number of pairs of queens which threaten each other.

Integer `m` in the code represents the number of the population held in every generation.

List `gen` stores the answers of the current generation.

`mRate` represents the ["Mutation Rate"](https://en.wikipedia.org/wiki/Mutation_rate).

The main loop iterates the generations.

### Output:
Outputs the corresponding permutation, and an image for better visual understanding.

## My Improvisation:
At first level, it randomly generates some permutations, and let them evolve for a little bit (Not long.) Then it saves this "little evolved" population. Then again, it generates some random permutations, and again let that evolve for a little and so on... It repeats this process several times. So, this prevents the populations to get "narrow".

At second and levels above, it randomly chooses from the previous level (just like first level, but instead of generating new permutations, it chooses from previous level.) And let them evolve a little bit but not much! And so on...

I got this idea from the structure of Segment Tree:
<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130359662-f19c6aea-e12b-41b0-88db-90404dd35358.png" width="600" />
</p>

This makes it like hydraulic press! It's slower, but it will penetrate through the hardest of problems! (Little bit exaggerated.)

Here's it solve this problem for `n = 1000` (In 12 Minutes):
<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130361012-17c47b2e-300b-4b02-a77f-dec548b1ea37.png" width="600" />
</p>

The solution (permutation) for `n = 1000` is present in the notebook.

