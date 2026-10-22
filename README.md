# Akshat Valse

Undergraduate researcher at Iowa State University, studying Statistics, Mathematics, Computer Science, and Data Science.

I work on the stochastic foundations of machine learning: the theory of stochastic differential equations, applied to the algorithms that now generate and sample. A diffusion model is a reverse-time SDE. Stochastic gradient descent and its Langevin variants are diffusions in a rough loss landscape. The connecting question is what can actually be proved about the objects practitioners already use, in place of heuristics.

NOTE: ALL RESEARCH RESULTS ARE CONFIDENTIAL PENDING PUBLIC RELEASE OF THE PAPERS.

I only have a general overview of what my work entails as of now to preserve confidentiality requirements and I am unable to accommodate requests to elaborate further about any active project beyond what is already public on my personal website and in their respective repos.

**[akshatvalse.com](https://akshatvalse.com)** — every figure there is a live simulation rather than a recording, and each one is graded against a closed-form answer.

### Current work

**[Langevin sampling, discretisation bias, and transport coefficients](https://akshatvalse.com/research)**
MALA and projected Euler–Maruyama samplers for overdamped Langevin dynamics, staged from a 1D periodic potential up to a solvated ion in a 3D Lennard-Jones bath. The Lifson–Jackson diffusivity `D = 1/I₀(1)² ≈ 0.62386` is exact, so it benchmarks the estimators before anything scales up. With David Herzog.

**[Rare events in the mean-field JSQ(d) model](https://akshatvalse.com/research)**
Large-deviation-guided importance sampling for join-the-shortest-queue systems. These probabilities are small enough to defeat direct simulation, so the estimator has to be checked against something that is not itself an estimate: where it is still feasible, uniformizing the killed chain reduces the question to linear algebra and gives ground truth with no sampling error. With Ruoyu Wu.

**[Stability of neural network PDE solvers](https://akshatvalse.com/research)**
Conservation in a cell-average neural network solver is architectural. Stability is not, and the training loss does not separate the networks that stay stable over long rollouts from the ones that come apart. I am working on whether that can be told from a trained network alone. Joint with Jue Yan and Mengyuan Yang.

**[Metastable failures in prefix-cached LLM agent serving](https://github.com/AkshatValse/Nova-Research-Overview)**
An agent re-sends its whole growing conversation on every turn, and a serving engine keeps that shared prefix in a GPU KV cache so follow-up turns stay cheap. When too many sessions compete for the cache, a session evicted during a tool call has to recompute everything, which keeps the cache full and evicts the next one. The question is whether a short burst can push a healthy server into a self-sustaining slow state, and which admission and scheduling mechanisms prevent it. A discrete-event simulator, a queueing-theoretic thrashing-curve model, and real-engine experiments on SGLang over A100s on ISU's Nova cluster, with predictions registered before each run. With Ali Jannesari, SwaPP Lab.

**[Online calibration of neural volatility forecasts with early, one-sided feedback](https://github.com/AkshatValse/neural-forecasting-research-overview)**
A forecast of a cumulative quantity is only scored when its horizon ends, so every online calibration method learns one full horizon late. But the increments are non-negative, so if the running sum crosses the issued bound early, the miss is certain immediately while coverage is confirmed only at the end. A model-agnostic layer on top of any quantile forecaster credits those certain early misses and keeps explicit accounts of forecasts still pending. Whether that recovers faster after a volatility jump than delayed-feedback conformal baselines, without widening the bounds the rest of the time, is the question; the coverage guarantee is proved and checked numerically. With Hongyang Gao.

**Reliability of tool-using agents**
When an agent stalls, when is restarting it worth more than waiting, and how do you estimate the probability of a failure too rare for direct simulation to reach? Two pilots on real agents, one on restart policies and one on rare failures, with the direction still being chosen. With Yang Li.

### Code

**[langevin-samplers](https://github.com/AkshatValse/langevin-samplers)**
What you give up by dropping the Metropolis correction. On a Gaussian target the unadjusted chain is a coordinatewise AR(1) whose stationary law is exact, `v(h) = s²/(1 - h/2s²)`, so the measured discretization bias can be checked against a formula instead of against a longer run of itself. Covers the first-order Wasserstein rate, what the correction costs in acceptance rate, and a metastable mixture where correcting the bias buys nothing.

**[akshatvalse-site](https://github.com/AkshatValse/akshatvalse-site)**
The site. Four hand-written simulations on canvas with no plotting or physics libraries, each with a verification script that grades it against a closed form.

Work with collaborators stays in private repositories until it is submitted.

### Tools

Python (NumPy, SciPy, PyTorch, matplotlib), C, R, LaTeX, git. I keep simulations as staged pipelines with recorded seeds and parameter sidecars, so every figure regenerates from saved results without re-running the sampler.

### Elsewhere

- [akshatvalse.com](https://akshatvalse.com) and [CV](https://akshatvalse.com/cv)
- avalse@iastate.edu
- [LinkedIn](https://linkedin.com/in/akshat-sachin-valse)

Licensed private pilot, certificated at seventeen, which is the earliest age the FAA allows.
