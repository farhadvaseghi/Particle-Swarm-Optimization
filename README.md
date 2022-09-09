
# Particle Swarm Optimization

## Particle Swarm
Particle Swarm Optimization was proposed by Kennedy and Eberhart in 1995. As mentioned in the original paper, sociobiologists believe a school of fish or a flock of birds that moves in a group “can profit from the experience of all other members”. In other words, while a bird flying and searching randomly for food, for instance, all birds in the flock can share their discovery and help the entire flock get the best hunt.
While we can simulate the movement of a flock of birds, we can also imagine each bird is to help us find the optimal solution in a high-dimensional solution space and the best solution found by the flock is the best solution in the space. This is a heuristic solution because we can never prove the real global optimal solution can be found and it is usually not. However, we often find that the solution found by PSO is quite close to the global optimal.
<p align="center">
  <kbd>
   <img src="flocking.PNG"  width="700" height="500">
</kbd>
</p>




PSO is best used to PSO is best used to find the maximum or 
minimum of a function defined on a multidimensional vector space.
Assume we have a function f(x) that produces a real value from a
vector parameter x (such as coordinate (x, y) in a plane) and x
can take on virtually any value in the space (for example, f(x) 
is the altitude and we can find one for any point on the plane), 
then we can apply PSO. The PSO algorithm will return the parameter  
x it found that produces the minimum f(x).

Similar to the flock of birds looking for food, we start with a 
number of random points on the plane (call them particles) and
let them look for the minimum point in random directions.
At each step, every particle should search around the minimum 
point it ever found as well as around the minimum point found
by the entire swarm of particles. After certain iterations, 
we consider the minimum point of the function as the minimum 
point ever explored by this swarm of particles.



## Algorithm Details
'Particle Swarm Optimization' locates the minimum of a function by creating a number of 'particles'. These particles store their best position as well as also storing the global best position. 
It is this combination of local and global information that gives rise to 'swarm intelligence'.

Within an iteration, a particle will update it's position slightly towards both the swarm best and slightly towards it's personal best. With eventually the particles converging on (hopefully) the global minimum.

Mathematically this position update is defined as follows: 

 <p align="center">
   <img src="https://render.githubusercontent.com/render/math?math=v_i^{t %2B 1}=\omega v_i^t %2B \phi_br_b(x_{i_b}-x_i) %2B \phi_gr_g(g_b-x_i)">
 </p>
  <p align="center">
   <img src="https://render.githubusercontent.com/render/math?math=x_i^{t %2B 1}=x_i^t %2B v_i^t">
   </p>
   
These equations become clear when presented in a simple 2 variable scenario: 
<p align="center">
<img src="https://github.com/TomRSavage/ParticleSwarm/blob/master/PS1.png" width="400"> <img src="https://github.com/TomRSavage/ParticleSwarm/blob/master/PS2.png" width="400">
</p>

Initially every particle is given a random velocity vi, and the function is evaluated for every particle. 
Each particle is now 'aware' of it's previous best position as well as the global best position. On the first iteration it's previous best position is obviously it's current position so this term doesn't come into play until the second iteration. 

It's current velocity is first scaled by a factor of w in order to ensure particle velocities don't grow exponentially over each iteration.

The term <img src="https://latex.codecogs.com/gif.latex?\phi_br_b(x_{i_b}-x_i)" title="\phi_br_b(x_{i_b}-x_i)" /> then represents the vector from the particles position, towards it's previous best position. It is scaled by a constant <img src="https://latex.codecogs.com/gif.latex?\phi_b" title="\phi_b" /> (Here I've sometimes referred to this as c1) and a random value <img src="https://latex.codecogs.com/gif.latex?r_b" title="r_b" /> between 0 and 1 (uniformly distributed). This random scaling provides the stochastic element of this optimization scheme.

Likewise <img src="https://latex.codecogs.com/gif.latex?\phi_gr_g(g_b-x_i)" title="\phi_gr_g(g_b-x_i)" /> represents the vector from the particles position towards the swarms best position, again scaled by a constant <img src="https://latex.codecogs.com/gif.latex?\phi_g" title="\phi_g" /> and a random variable <img src="https://latex.codecogs.com/gif.latex?r_g" title="r_g" />. Varying these phi (or c) parameters effect how locally or globally the particle explores the search space. A higher value will provide a larger vector and therefore the particle will take into account that aspect more than another. 

It's seen in the second graph the effect of lining up these vectors and then the final step of moving the particle to it's new position. 

<kbd>
   <img align="center" src="https://github.com/TomRSavage/ParticleSwarm/blob/master/Sty.gif" width="600">
</kbd>



