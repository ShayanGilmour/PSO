# Particle Swarm Optimization
Minimizing/Maximizing the value of a function.

Long story short: There are `n` particles moving in the domain of the target function. Each particle has a position and a velocity vector. The velocity of
each particle changes in regards to the point where the "best" value of the function was found globaly (among every particle), the point where the "best" value of the
function was meet by this particle, and inertia and a randomness. Each of these parameters has a constant multiplier too.

Here, I've tried to find the minimum of the below cost function:

<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130462641-07e74a0a-60f0-4b67-9ae3-012716ca29d9.png" width="600" />
</p>

It's rather a "simple" function as its domain is a subset of the 2 dimensional plane. For such functions, Google can easily find the minimum for you! But still, here's how the function looks like:

<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130463029-94265ed7-1ad8-46e4-8dd1-9b3845cb5bd3.png" width="600" />
</p>


### Input:
Function `f` is the cost function which using PSO, this code tries to minimize it.

### Process:
Global Variables:
 + `inertia`: Inertia's constant
 + `pbc`: Personal best constant
 + `gbc`: Group best constant
 + `gbcor`: Group best coordinations
 + `gbv`: Group best value
 + `n`: number of particles
 + `maxV`: Maximum of velocity a particle can obtain

There's a class called `Particles`, which has the following variables:

+ `cor`, which stores the current coordinate of the particle.
+ `bestCor`, which stores the "best" coordinate this particle ever had.
+ `best`, which stores the value of the function `f` at coordinate `bestCor`.
+ `v`, which is the velocity vector of this particle.

For the above function, this is the positioning of the particles at different times of the calculation:
<p float="left">
  <img src="https://user-images.githubusercontent.com/12760574/130467986-e1e8dcf0-0d36-484a-b82f-4bc529641928.png" width="600" />
</p>

As can be observed from the image of the function, the potential candidates for the function's minimum is placed on the 4 corners of the `x` and `y` plane in range `(-10, 10)`.

### Output:
Outputs the minimum/maximum value of the function `f` that particles have found.
