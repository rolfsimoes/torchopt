
<!-- README.md is generated from README.Rmd. Please edit that file -->

# torchopt

<!-- badges: start -->
<!-- badges: end -->

The goal of `torchopt` is to provide deep learning optimizers proposed
in the literature to be available in R language for torch.

## Installation

You can install the development version of `torchopt` like so:

``` r
# library(devtools)
install_github("e-sensing/torchopt)
```

## Example

This following example shows you how to use `AdamW` optimizer proposed
by Loshchilov & Hutter (2019):

``` r
library(torchopt)
## basic example code
```

## Provided optimizers

`torchoptimizers` package provides the following R implementation of
torch optimizers:

-   `optim_adamw()`: AdamW optimizer proposed by Loshchilov & Hutter
    (2019). We ported it from the `pytorch` code developed by Collin
    Donahue-Oponski available at
    <https://gist.github.com/colllin/0b146b154c4351f9a40f741a28bff1e3>

-   `optim_yogi()`: Yogi optimizer proposed by Zaheer et al.(2019). We
    ported it from the `pytorch` code developed by Nikolay Novik
    available at
    <https://github.com/jettify/pytorch-optimizer/blob/master/torch_optimizer/yogi.py>

-   `optim_adabound()`: Adabound optimizer proposed by Luo et al.(2019).
    The original implementation is available at
    <https://github.com/Luolc/AdaBound>.

-   `optim_madgrad()`: Momentumized, Adaptive, Dual Averaged Gradient
    Method for Stochastic Optimization (MADGRAD) optimizer proposed by
    Defazio & Jelassi (2021). The function is imported from
    [https://CRAN.R-project.org/package=madgrad](madgrad) package and
    the source code is available at <https://github.com/mlverse/madgrad>

## Optimization test functions

You can also test optimizers using optimization test functions and
visualize them. Optimization functions are useful to evaluate
characteristics of optimization algorithms, such as convergence rate,
precision, robustness, and performance. `torchopt` provide some test
functions to give an idea about the different situations that
optimization algorithms can face when coping with optimization problems.

``` r
library(torchopt)
test_functions(test_fn = "beale")
```

<img src="man/figures/README-opt_fun-1.png" width="5" height="5" />

Use [https://CRAN.R-project.org/package=gifski](gifski) package to
generate an animated gif. In the following examples, we test each
optimizer using `"beale"` and `"rastrigin"` test functions.

-   `optim_adamw()`: AdamW optimizer proposed by Loshchilov & Hutter
    (2019). We ported it from the `pytorch` code developed by Collin
    Donahue-Oponski available at
    <https://gist.github.com/colllin/0b146b154c4351f9a40f741a28bff1e3>

``` r
# set manual seed
torch::torch_manual_seed(42)
test_optim(
    opt = optim_madgrad,
    opt_hparams = list(lr = 0.1),
    test_fn = "beale",
    steps = 100,
    bg_x_lim = c(-5, 5),
    bg_y_lim = c(-5, 5),
    plot_each_step = TRUE
)
```

<img src="man/figures/README-gif_opt-.gif" width="5" height="5" />

-   `optim_yogi()`: Yogi optimizer proposed by Zaheer et al.(2019). We
    ported it from the `pytorch` code developed by Nikolay Novik
    available at
    <https://github.com/jettify/pytorch-optimizer/blob/master/torch_optimizer/yogi.py>

-   `optim_adabound()`: Adabound optimizer proposed by Luo et al.(2019).
    The original implementation is available at
    <https://github.com/Luolc/AdaBound>.

-   `optim_madgrad()`: Momentumized, Adaptive, Dual Averaged Gradient
    Method for Stochastic Optimization (MADGRAD) optimizer proposed by
    Defazio & Jelassi (2021). The function is imported from
    [https://CRAN.R-project.org/package=madgrad](madgrad) package and
    the source code is available at <https://github.com/mlverse/madgrad>

## Acknowledgements

We thankful to Collin Donahue-Oponski <https://github.com/colllin>,
Nikolay Novik <https://github.com/jettify>, and Liangchen Luo
<https://github.com/Luolc> for proving pytorch code.

## References

-   Ilya Loshchilov, Frank Hutter, “Decoupled Weight Decay
    Regularization”, International Conference on Learning
    Representations (ICLR) 2019.
    <https://doi.org/10.48550/arXiv.1711.05101>

-   Manzil Zaheer, Sashank Reddi, Devendra Sachan, Satyen Kale, Sanjiv
    Kumar, “Adaptive Methods for Nonconvex Optimization”, Advances in
    Neural Information Processing Systems 31 (NeurIPS 2018).
    <https://papers.nips.cc/paper/8186-adaptive-methods-for-nonconvex-optimization>

-   Liangchen Luo, Yuanhao Xiong, Yan Liu, Xu Sun, “Adaptive Gradient
    Methods with Dynamic Bound of Learning Rate”, International
    Conference on Learning Representations (ICLR), 2019.
    <https://doi.org/10.48550/arXiv.1902.09843>

-   Aaron Defazio, Samy Jelassi, “Adaptivity without Compromise: A
    Momentumized, Adaptive, Dual Averaged Gradient Method for Stochastic
    Optimization”, arXiv preprint arXiv:2101.11075, 2021.
    <https://doi.org/10.48550/arXiv.2101.11075>