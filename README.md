# Akshat Valse

Undergraduate researcher at Iowa State University, studying Statistics, Mathematics, Computer Science, and Data Science.

I build reproducible simulations and numerical experiments in Python, with research spanning stochastic sampling, rare events, neural PDE solvers, and ML serving systems. My focus is connecting mathematical guarantees to implementations that can be checked against exact references.

I run research and engineering projects with coordinated AI agents (Codex, Claude, local models through Ollama, and Model Context Protocol tools): a planner splits the work among specialized agents that run in parallel, and automated tests and reproducible runs check what they produce, from problem formulation through implementation and validation.

Joint work stays private until it is submitted. Public projects and research summaries are linked below, and I am happy to discuss my contributions and methods.

**[akshatvalse.com](https://akshatvalse.com)** — every figure there is a live simulation rather than a recording, and each one is graded against a closed-form answer.

### Current work

**[Inside the Trap: prefix-cache collapse in LLM agent serving](https://github.com/AkshatValse/surviving-llm-stampede)**
An agent re-sends its whole growing conversation on every turn, and a serving engine keeps that shared prefix in a GPU KV cache so follow-up turns stay cheap. While sessions wait on tools, a burst of new ones can evict that cache and tip the engine into a trap: every turn misses and the backlog does not drain, at a load it served before. In registered paired tests on two engines (SGLang and vLLM), two GPUs (A100 and H200) and two models, a 200-session burst left the engine at zero hits to the end of the run in all 30 burst runs (the registered rule, which also requires a growing backlog, was met at 9 of 10 rates), every matched no-burst run stayed good, and a session cap prevented the trap in all 30 capped runs. The paper proves a renewal law for an idealized trapped server, under which, for the workload studied, the throughput measured in a trap overstates the load at which it drains; checks it retrospectively against 57 stuck runs and in blind tests; and shows that a session cap rescued 9 of 9 established traps without shedding a session. Preprint with Ali Jannesari (SwAPP Lab), [arXiv:2611.08902](https://arxiv.org/abs/2611.08902), November 2026; the code, all real-engine data and every registration are public.

**[Langevin sampling, discretization bias, and transport coefficients](https://akshatvalse.com/research)**
MALA and projected Euler–Maruyama samplers for overdamped Langevin dynamics, staged from a 1D periodic potential up to a solvated ion in a 3D Lennard-Jones bath. The Lifson–Jackson diffusivity `D = 1/I₀(1)² ≈ 0.62386` is exact, so it benchmarks the estimators before anything scales up. With David Herzog.

**[Rare events in the mean-field JSQ(d) model](https://akshatvalse.com/research)**
Large-deviation-guided importance sampling for join-the-shortest-queue systems. These probabilities are small enough to defeat direct simulation, so the estimator has to be checked against something that is not itself an estimate: where it is still feasible, uniformizing the killed chain reduces the question to linear algebra and gives ground truth with no sampling error. With Ruoyu Wu.

**[Stability of neural network PDE solvers](https://akshatvalse.com/research)**
Conservation in a cell-average neural network solver is architectural. Stability is not, and the training loss does not separate the networks that stay stable over long rollouts from the ones that come apart. I am working on whether that can be told from a trained network alone. Joint with Jue Yan and Mengyuan Yang.

**[Online calibration of neural volatility forecasts with early, one-sided feedback](https://github.com/AkshatValse/neural-forecasting-research-overview)**
A forecast of a cumulative quantity is only scored when its horizon ends, so every online calibration method learns one full horizon late. But the increments are non-negative, so if the running sum crosses the issued bound early, the miss is certain immediately while coverage is confirmed only at the end. A model-agnostic layer on top of any quantile forecaster credits those certain early misses and keeps explicit accounts of forecasts still pending. Whether that recovers faster after a volatility jump than delayed-feedback conformal baselines, without widening the bounds the rest of the time, is the question; a coverage guarantee is written up as a proof draft and tested numerically. Advised by Hongyang Gao.

**Reliability of tool-using agents**
When an agent stalls, when is restarting it worth more than waiting, and how do you estimate the probability of a failure too rare for direct simulation to reach? Two planned real-agent pilots, one on restart policies and one on rare failures, with the direction still being chosen. Current validation uses mock environments. With Yang Li.

### Code

**[surviving-llm-stampede](https://github.com/AkshatValse/surviving-llm-stampede)**
Everything behind the Inside the Trap preprint: the simulator, load generator, analysis and model code, all real-engine data with its job logs, and every registration with the GitHub push records that date it. Each number in the paper traces to a file and a commit or Slurm job.

**[langevin-samplers](https://github.com/AkshatValse/langevin-samplers)**
What you give up by dropping the Metropolis correction. On a Gaussian target the unadjusted chain is a coordinatewise AR(1) whose stationary law is exact, `v(h) = s²/(1 - h/2s²)`, so the measured discretization bias can be checked against a formula instead of against a longer run of itself. Covers the first-order Wasserstein rate, what the correction costs in acceptance rate, and a metastable mixture where correcting the bias buys nothing.

**[akshatvalse-site](https://github.com/AkshatValse/akshatvalse-site)**
The site. Four hand-written simulations on canvas with no plotting or physics libraries, each with a verification script that grades it against a closed form.

### Tools

Python (NumPy, SciPy, pandas, PyTorch, matplotlib), C, R, LaTeX, git, Slurm. I keep simulations as staged pipelines with recorded seeds and parameter sidecars, so every figure regenerates from saved results without re-running the sampler.

### Elsewhere

- [akshatvalse.com](https://akshatvalse.com) and [CV](https://akshatvalse.com/cv)
- avalse@iastate.edu
- [LinkedIn](https://linkedin.com/in/akshat-sachin-valse)

Licensed private pilot, certificated at seventeen, which is the earliest age the FAA allows.
