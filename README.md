# CML Serum Crotisol Level Prediction 

The given data consists of a sprase vector `u` which was observed at times `tu`. Along with it is given the partial data for the serum cortisol concentraion `y` which was sampled at regular intervals `ty`. [This paper](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0085204) defines a model (with the unkowns `theta_1` and `theta_2` as the model parameters) that establishes a realtionship between the discrete `y` and sparse `u`

The task reconstruct the complete y based on the data available. To do this, we first compute optimal values of the parameters `theta_1` and `theta_2` that give the least error rate. Once we have these values, we reconstruct a continous `y` as per the model. 

## Methodology

Scipy and Numpy libraries were used to solve this problem, we first formulate an optimization problem for the model and try to minimize the objective function - `|y - A*y_0 - B*U|^2` in our case. 

The code is presented in a Jypyter notebook and the implementation is as follows

* Read the given data from the file and process it acc to our use case
* Define the model as per the paper and the objective function as mentioned above. 
* Initialize the parameters `theta_1` and `theta_2` with any random non equal values.
* Use `scipy.minimize` [method](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.minimize.html) to minimize the objective function over the parametrs `theta_1` and `theta_2`. The `Nelder-Mead` [optimization](https://docs.scipy.org/doc/scipy/reference/optimize.minimize-neldermead.html#optimize-minimize-neldermead) was used to solve this problem. 
* Once we obtain the estimated values of `theta_1` and `theta_2`, we use that to estimate the complete signal of `y`.
* We plot the `predicted_y` against `observed_y` on the notebook and present it at the end. 

## Results 

* The `theta_1` and `theta_2` values were initialzed randomly but always convered at a single value close to ~ `0.73`.
* The `estimated_y` was plotted against the `observed_y` and is shown in the plot marked at the end of the Python notebook. 

## References 

[1] [Deconvolution of Serum Cortisol Levels by Using Compressed Sensing]( https://doi.org/10.1371/journal.pone.0085204)

[2] [Nelder-Mead method](https://en.wikipedia.org/wiki/Nelder%E2%80%93Mead_method)

