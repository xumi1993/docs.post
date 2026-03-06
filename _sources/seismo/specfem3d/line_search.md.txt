# How to determine an optimal step length

A suitable step length will help to fast convergence of objective function. In practice, this processing may require to test a large number of step lengths, which can be huge computational costs. Thus, the Wolfe condition is used to constrain range of step length. For each iteration, we assume {math}`\phi(\alpha)` is a function of the objective function {math}`\chi` in recept to the step length {math}`\alpha`. The {math}`\phi(0)=\chi(\mathbf{m})`

:::{math}
\phi(\alpha) = \chi(\mathbf{m}+{\alpha}{\nabla}\phi(0))
:::

In practice, preconditioner will be applied on the misfit kernel{math}`{\nabla}\phi(0)`, and the gradient will be fixed with some specified optimization method, such L-BFGS method. Thus the above equation is also given by

:::{math}
\phi(\alpha) = \chi(\mathbf{m}+{\alpha}\mathbf{g}(\mathbf{m}))
:::

where the {math}`\mathbf{g}(\mathbf{m})` is the direction fixed by preconditioner, smooth and L-BFGS.

## Armijo rule and curvature

Armijo rule define the upper limitation of the step length.

:::{math}
\phi(\alpha) \le \phi(0)+{c_1}{\alpha}\mathbf{g}^T{\nabla}\phi(0)
:::

curvature define the lower limitation of the step length

:::{math}
-\mathbf{g}^T  {\nabla}\phi(\alpha) \le -c_2\mathbf{g}^T {\nabla}\phi(0)
:::

Parameters {math}`c_1` and {math}`c_2` control more or less restrictive in term of accepting step length. Nocedal & Wright (2006) suggest a selection of {math}`c_1 = 0.1` and {math}`c_2 = 0.9`.

:::{note}
The objective function may be convergence when the step length is not satisfy the curvature condition. If the specification is limited solely to iteration numbers, it is only necessary to employ the Armijo rule, because the computation of gradient of the objective function in curvature condition is very expensive. 
:::
