# Homework 2
## Bowen Zhao <br> UNI: bz2594

### Chain Rule & Weight Updates
The network defined in lecture is $$z = w_1 x + b_1,\quad h = ReLU(z), \quad y = w_2 h + b_2$$
The loss function is $$L = \frac{1}{2}(y - t)^2$$
By applying the chain rule, we can find $\frac{\partial L}{\partial w_1}$ by 
$$\frac{\partial L}{\partial w_1} = \frac{\partial L}{\partial y} \frac{\partial y}{\partial h} \frac{\partial h}{\partial z} \frac{\partial z}{\partial w_1}$$

To find the individual derivatives:

$$\frac{\partial L}{\partial w_1}  = \frac{1}{2} \times 2(y - t) = y - t$$

$$\frac{\partial y}{\partial h} = w_2$$

$$\frac{\partial h}{\partial z} = \begin{cases} 1, z > 0 \\ 0, z \le 0\end{cases}$$

$$\frac{\partial z}{\partial w_1} = x$$

Thus
$$\frac{\partial L}{\partial w_1} = \begin{cases}(y - t) w_2  x,& z = w_1 x + b_1 > 0 \\ 0,& z = w_1 x + b_1 \le 0\end{cases}$$


### Gradient Descent
The gradient of a function $L$ is the vector constituted by $\frac{\partial L}{\partial x}$ and $\frac{\partial L}{\partial y}$. This vector, the gradient, points to the direction where the function $L$ increases at the fastest rate. Hence, its opposite direction is the fastest decreaseing direction. If the function $L$ is the loss function, the negative gradient takes us to a local minimum that minimizes the loss function. The gradient tells us the direction to minimize the loss function, and a step size small enough makes sure that we are approaching the local minimum.

So we have this weight update rule taking the learning rate $\eta$ into consideration: $$w_{new} = w_{old} - \eta \frac{\partial L}{\partial w}$$

Intuitively speaking, when the learning rate is too large, the loss function may cross the local minimum, and then the new gradient points back, but again the too-big learning rate causes the function to pass the local minimum again, and this cycle repeats. Oscillation then occurs. 

When this jumping back-and-forth happens and the loss becomes larger, gradient descent fails to converge. A learning rate that is large enough can take the loss fucntion away from the local minimum, thus leading to divergence.

For example, $$ L(w) = w^2 \quad \frac {\partial L}{\partial w} = 2w$$
If $$\eta = 0.1$$
then $$w_{new} = 0.8w_{old}$$
so $w$ gradually approaches 0


But if $$\eta = 1.1$$
then $$w_{new} = -1.2w_{old}$$
and the $w$ gets larger and larger and diverges.
This illustrates how a large-enough $\eta$ could lead to the failure of gradient descent.