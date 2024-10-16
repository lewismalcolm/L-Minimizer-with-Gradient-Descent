# L-Minimizer-with-Gradient-Descent
Finding the minimizer of L using Gradient Descent with Fixed Stepsize and Backtracking Algortihm

    def g(b):
     b0,b1 = b
     beta_b0 = -(1/3)*((3.8 - b0 -5*b1) + (6.5 - b0 - 6*b1) + (11.5 - b0 -
    7*b1))
     beta_b1 = -(1/3)*((3.8 - b0 -5*b1)*(5) + (6.5 - b0 - 6*b1)*(6) + (11.5 -
    b0 - 7*b1)*(7))
     return np.array([beta_b0, beta_b1])
This function calculates the gradient vector of the function g(β) by computing the partial
derivatives of β0 and β1 and returns them as an array

# L minimizer Gradient Descent fixed stepsize

In order to find the minimizer of Ⅼ using gradient descent with fixed stepsize, we create a function
called gd. This function takes the arguments: start, f, gradient, step_size, maxiter, and tolerance
tol. In this function step_size is fixed and set at 0.01, maxiter is the number of iterations it takes to
reach convergence, and tol is used to check when convergence is reached. This method applies
gradient descent with fixed stepsize to find the minimizer of L.

    def gd(start, f, gradient, step_size, maxiter, tol=0.01):
     step = [start] ## tracking history of x
     x = start
     k=0
     for i in range(maxiter):
     diff = step_size*gradient(x)
     if np.all(np.abs(diff)<tol):
    
     break
     k=k+1
     x = x - diff
     fc = f(x)
     step.append(x) ## tracking
    
     print('iterations = ', k)
     return step, x
In this function we use step to calculate the path taken, and then we set the value of x to the
starting point. We set k=0 to calculate the number of iterations taken to reach convergence. We
multiply the stepsize by the gradient at x to determine the change we then check to see if the
convergence is reached by checking if diff is less than the tolerance. If it is not less than the
tolerance k and x are updated and we repeat these steps until the diff is less than tol.

      history, solution = gd(np.array([1,5]),f,grad_f,0.01,100)
      #print('history =', history)
      print('solution =', solution)
      iterations = 11
      solution = [0.34914044 1.22230655]

We find that minimizer of L = [0.34914044 1.22230655] and it took 11 iterations to reach
convergence. The final values of β0 are 0.41631307 and β1 0.74608277.

# L minimizer with Gradient Descent Backtracking Algorithm

In order to find the minimizer of Ⅼ using gradient descent with backtracking algorithm, we create
a function called steepestdescent. This function takes the arguments: f, df. step_size, x0, maxiter,
and tolerance tol. Step_size starts at 1 and is reduced by a factor β until the stopping condition,
maxiter is used to keep track of how many iterations it took to reach convergence, and tol checks
for when convergence is reached.

      def steepestdescent(f,df,step_size,x0,tol=1.e-3,maxit=100):
       x = x0
       r = df(x0)
       iters = 0
       while ( np.abs(npl.norm(r))>tol and iters<maxit ):
       lambda_k = step_size(x)
       x = x - lambda_k * r
       r = df(x)
       iters += 1
       print('iterations =', iters)
       return x, iters
 
In this function we start at the initial value x0 and set r =gradient at x0. We set iters = 0 to start
the count of how many iterations it takes to reach convergence. We then update the stepsize to
determine how far we go in the opposite direction of the gradient. X is then updated and used to calculate the new value of the gradient r at the value of x. The iters counter is also updated and this is done until the norm of gradient r is greater than tol.

        x0 = np.array([2.0,1.0])
        x, iters =steepestdescent(f, df, step_size,x0, tol = 1.e-8, maxit = 7)
        print('solution = ', x)
        print('iteration =', iters)
        iterations = 7
        solution = [1.96723136 0.93832251]

We find that the minimizer of L = [1.96723136 0.93832251] and it took 7 iterations to reach
convergence. The final value of β0 = 0.33049973 and β1 = 0.04188008


