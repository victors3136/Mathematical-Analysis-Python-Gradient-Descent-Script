# Mathematical Analysis Python Gradient Descent Script
Small gradient descent plotting script I made as part of my Mathematical Analysis Course during my first semester of univeristy.

# Here is the assignment text
 Consider the quadratic function f : R^2 → R, f (x, y) = 1/2* (x^2 + b*y^2) with b > 0  
 and the gradient descent algorithm for finding its minimum <br />  
  (x_(k+1), y_(k+1)) = (x_k, y_k) − s_k* ∇f (x_k, y_k), <br />  
 where the step size s_k > 0 is chosen (exact line search) to minimize the function  
  ϕ(s) = f (x_(k+1), y_(k+1)) = f ((x_k, y_k) − s*∇f (x_k, y_k)), ϕ′(s_k) = 0.<br />  
  For b = 1, 1/2 , 1/5 , 1/10, plot some gradient descent iterations and the relevant contour lines of f .  

# How we go about solving this
∇f = (f1, f2), where f1: R → R, f1(x) = d(1/2*x^2+ 1/2*b*y^2)/dx = x <br />  
                      f2: R → R, f1(y) = d(1/2*x^2+ 1/2*b*y^2)/dy = b*y <br />  
∇f gives us the direction in which we must move to minimise the function, while s_k gives us the size of the step.  
We pick s_k so that each step is perpendicular on the one before and the one after.<br />  
ϕ is a helper function which allows us make sure that the steps are perpendicullar on eachother.<br />  
From Analysis we know that always the fastest way to descend is directly perpendicullar on the level curve.  

# Example output
![image](https://github.com/victors3136/UniWorkSem1-GradientDescent/assets/115093754/d329c54c-617b-433d-a492-3bfb7f13b684)
![image](https://github.com/victors3136/UniWorkSem1-GradientDescent/assets/115093754/024e7f8d-bcae-4454-906d-656483c88ed3)
![image](https://github.com/victors3136/UniWorkSem1-GradientDescent/assets/115093754/8d301b94-66c2-48c6-afbf-98c343b3f948)

# Acknowledgements
This project was accomplished with the knowledge I gained during the Mathematical Analysis course taught by Professor Mihai Nechita and Fundamentals of Programming course taught by Professor Arthur Molnar as part of the Bachelors Degree of Computer Science at Babes Bolyai University. The actual code was made under the supervision and with the help of Professor Mihai Nechita.<br />  
