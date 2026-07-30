# Akshat Valse

Undergraduate researcher at Iowa State University, studying Statistics, Mathematics, Computer Science, and Data Science.

I work in stochastic analysis: stochastic differential equations, Langevin dynamics, and sampling. I am also interested in where that theory meets machine learning, particularly diffusion and score-based generative models, and in the numerical analysis of PDE solvers that have a network inside them.

### Current work

Write-ups for all three are in [AkshatValse/research](https://github.com/AkshatValse/research).

**[Stability of neural network PDE solvers](https://github.com/AkshatValse/research/blob/main/cann-stability.md)**
Conservation in a cell-average neural network solver is architectural. Stability is not, and the training loss does not separate the networks that stay stable over long rollouts from the ones that come apart. I am working on whether that can be told from a trained network alone. Joint with Jue Yan and Mengyuan Yang.

**[Rare events in the mean-field JSQ(d) model](https://github.com/AkshatValse/research/blob/main/jsq-rare-events.md)**
Large-deviation-guided importance sampling for join-the-shortest-queue systems, with exact and Monte Carlo numerics used to benchmark the estimator against the analytic rate function.

**[Langevin samplers](https://github.com/AkshatValse/research/blob/main/langevin-samplers.md)**
What you give up by dropping the Metropolis correction. On a Gaussian target the unadjusted chain is a coordinatewise AR(1) whose stationary law is exact, `v(h) = s²/(1 - h/2s²)`, so the measured discretization bias can be checked against a formula instead of against a longer run of itself. Covers the first-order Wasserstein rate, what the correction costs in acceptance rate, and a metastable mixture where correcting the bias buys nothing.

### Tools

Python (NumPy, SciPy, matplotlib), Java, R, LaTeX, git. I keep simulations as staged pipelines with recorded seeds and parameter sidecars, so every figure regenerates from saved results without re-running the sampler.

### Elsewhere

- [LinkedIn](http://linkedin.com/in/akshat-sachin-valse)
- [Personal site](https://sites.google.com/view/akshatsachinvalse/home)
- akshatsachinvalse@gmail.com

Licensed private pilot, certificated at seventeen, which is the earliest age the FAA allows.
