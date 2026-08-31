# Mental models: from software engineering to ML and AI-native systems

Insights captured while working through *Grokking Machine Learning* (Serrano) with the
interactive playgrounds in this folder (`grid-world-rl.html`, `linear-regression-lab.html`).
Two sets: the paradigm shifts from traditional software engineering to ML, and how the same
worldview maps onto building AI agents, applications, and evals.

---

## Part 1 — The paradigm shifts (SWE → ML)

Learning ML isn't about missing math background. It's that ML quietly inverts several
assumptions traditional software engineering trains into you. Name the inversions and the
concepts stop being slippery.

### 1. You don't write the behavior — you write the feedback

In traditional software, behavior is *specified*: the program does what you wrote, and a bug
means you wrote the wrong logic. In ML, you write a tiny fixed loop plus a *score* (reward,
error), and the behavior grows out of the interaction between score and data.

- Nobody wrote "avoid the dragon" — the −50 wrote it.
- Nobody wrote "charge $50 per room" — the misses wrote it.

**Corollary:** when an ML system misbehaves, you usually debug the *incentives* (reward,
error function, data), not the code. The outlier experiment proved this: identical code, but
the square error's incentives dragged the line somewhere the absolute error's didn't.

### 2. Correctness becomes convergence

SWE thinks in binary: passes or fails, provable, done. ML thinks in trajectories: the answer
is *approximately right and improving*, never finished — you decide when to stop by watching
a curve flatten. Testing becomes measurement (RMSE, return-per-episode), and "is it working?"
becomes "is the curve falling?" Charts are not decoration; they are the replacement for
assertions.

### 3. The program is boring; the state is everything

Both playgrounds run on ~five lines of real logic: `pick, act, score, nudge, repeat`. All the
intelligence lives in the evolving numbers (the Q table; the two knobs m and b). The real
"program" is written *by the data into the parameters*; the code is just the loom it's woven
on. Deepest inversion for a SWE: you're used to logic being the asset and data flowing
through it — here data is the author and the parameters are the artifact.

### 4. The home intuition is geometry, not logic

SWE reasons in booleans, branches, cases. ML reasons in *landscapes*: where am I, which way
is downhill, how big a step. Hold "every configuration of knobs is a point on an error
surface" and huge swaths of ML collapse into one picture:

- learning rate = stride length
- convergence = settling into a valley
- local minima = the wrong valley
- regularization = reshaping the terrain

This picture scales unchanged from 2 knobs to 2 billion.

### 5. Debugging becomes instrumentation

You can't breakpoint your way through 10,000 epochs. You read traces, curves, heatmaps —
closer to observability/ops than to stepping through code. The anatomy strips and narrated
trace panels in these playgrounds *are* the ML debugging discipline, hand-made.

### 6. Two nested loops of authorship

The machine writes the **parameters** (inner loop); you tune the **hyperparameters** by
experiment (outer loop: run → observe → adjust → run again). ML engineering is less like
construction, more like experimental science: hypothesis, run, instrument reading,
intervention.

### The two-spaces duality (data space vs parameter space)

The data plot and Mount Errorest are the same object seen twice:

- **Data space** (feature space): axes = feature & label; houses are points; a model is a line.
- **Parameter space** (weight space): axes = the knobs (m, b); a model is a *point*; the whole
  plane is the space of **all possible models** — almost all of them bad.
- The height/color at every point is that model's error **measured against the data** — the
  data is the judge; no "best model" is needed to draw the map.
- Add the height and it's called the **loss landscape / error surface**. All the field's
  hill vocabulary (gradient descent, hill climbing, local minima, plateaus, saddle points,
  fitness landscapes) is literal geometry on this picture.
- The map is a teaching luxury: drawable only with 2 knobs and tiny data. Real models
  (high-dimensional parameter space) make the map impossible — which is *why* gradient
  descent exists: stand at one point, feel the local slope through one miss, step downhill,
  in fog. (Caveat: in high dimensions true traps are rare; most flat spots are saddles.)
#### Where the landscape idea came from — six discoveries, layered

No single person invented this; science assembled it in layers, and each layer is a piece
used in the playgrounds:

- **Descartes (1630s)** laid the master trick under everything: *anything describable by
  numbers can be treated as a point in a space.* A line is two numbers (m, b), so a line is
  a point in a 2D plane. Sounds obvious now; it was one of the biggest ideas in the history
  of mathematics.
- **Legendre and Gauss (1805–1809)** invented **least squares** — fitting a line by
  minimizing summed squared misses. They *were* finding the bottom of the bowl, though they
  solved it with algebra in one shot rather than walking. For linear models the bowl is
  simple enough to solve exactly — that's why sklearn's `fit()` doesn't need epochs.
- **Cauchy (1847)** invented the walking: the **method of steepest descent** — "when you
  can't solve for the bottom, repeatedly step downhill." Gradient descent is nearly 180
  years old.
- **Physics (late 1800s: Gibbs, Boltzmann, building on Lagrange and Hamilton)** made
  **configuration space** a working tool — an entire system's state as a single point, so a
  system's evolution becomes a *path* through the space. The training trail on Mount
  Errorest is exactly this.
- **Sewall Wright (1932)** — an evolutionary biologist — drew the first true landscape
  picture: genes as coordinates, survival fitness as height, evolution as populations
  walking uphill on a **fitness landscape**. That's where the vivid hills-and-valleys
  imagery enters science, two decades before AI existed.
- **The neural-net era (Hopfield 1982; Rumelhart, Hinton & Williams' backprop paper, 1986)**
  imported it all into ML: **"error surface"** and **"energy landscape"** became the
  standard mental furniture, and backprop was pitched as exactly this — descending the
  error surface, just with millions of knobs.

The takeaway: nudging two sliders and watching a dot roll into a green valley stands on
Descartes' coordinates, Gauss's error-minimizing, Cauchy's descent, physics' configuration
space, and a biologist's mountains. The playground is small; the idea underneath it is one
of the most reused in all of science.

**Compressed intuition (my one line):**

> Every possible line is a single point on the m–b map, colored by how badly that line
> misses the houses — and training is just that point sliding downhill, one small nudge per
> miss, on a map it never gets to see.

### The unifying worldview

One update rule seen twice in two "different" fields:

```
Q ← Q + α × (target − Q)        // reinforcement learning
b ← b + h × (y − ŷ)             // linear regression
```

Same sentence: *keep most of what you believe, blend in a fraction of the evidence.*
Almost everything ahead — neural networks, embeddings, fine-tuning, RLHF — is the same
triple: **knobs + score + nudge downhill on a landscape nobody ever sees whole.** Only what
the knobs parameterize and how the score is defined changes.

Bonus intuitions earned along the way:

- **Learning rate ≠ error precision.** h is how much the model trusts one sample's miss.
  It bounds final *settling* precision (jump size on a hill), traded against speed.
  Nudge ∝ miss makes strides self-shrink near the valley; decay and adaptive optimizers
  (Adam, reduce-on-plateau) automate the human loop of "notice I'm just bouncing → shrink
  the jump."
- **Gradient descent finds *a* valley, not necessarily the deepest.** Linear regression's
  bowl has one valley; deep nets don't. Randomness in stochastic steps helps shake out of
  shallow dips.
- **The right h is found by experiment:** try powers of ten, keep the largest that doesn't
  explode, read the error curve (explodes = too big; crawls = too small; drops-then-flattens
  = right).

---

## Part 2 — The same worldview, applied to AI agents, applications, and evals

Working on agents/apps/evals with a SWE mindset feels disorienting because you keep looking
for the wrong logic — and there is no logic to be wrong. The ML worldview transfers almost
one-to-one:

### Your evals are the error function

Writing an eval suite is exactly what the −50 on the dragon and the squared miss were:
defining the score behavior will bend toward. The agent loop, like the training loop, is
trivially thin (observe, decide, call tool, repeat). Behavior emerges from a frozen model ×
the context you feed it × what your evals reward you for shipping.

**Corollary, verbatim:** when the agent misbehaves, suspect the incentives before the code —
the prompt that under-specifies, the context that's missing, the eval that doesn't cover the
case. The glue code is almost never where the bug lives.

### Eval design is reward design — Goodhart included

Grid world lesson: "set cost per step to 0 and the robot has no reason to hurry" — the score
under-specified the intent, so behavior satisfied the letter and ignored the spirit. Agents
do this constantly:

- eval rewards "answered the question" → confident wrong answers
- eval rewards "no errors thrown" → agents that silently skip work

Every gap between what the eval measures and what you actually want is a dragon-shaped hole
the agent will eventually find.

### Prompt iteration is gradient descent by hand

Change the prompt → run the eval suite → read the score → keep the change if it improved.
You are the optimizer; the eval score is your altitude; a prompt tweak is a step whose
direction you guessed. Free diagnostics from the descent picture:

- thrashing between prompt versions with no improvement = steps too coarse, or the eval too
  noisy to give a gradient
- slow steady gains = keep going
- an eval suite that's too small is a noisy altimeter — you can walk uphill while it reads
  "descending"

### Correctness is a distribution

One passing agent run proves nothing (one low-error point never proved the line fit). The
unit of truth is the pass rate over a suite; eval scores are your RMSE-per-epoch chart.
Single-run demos mislead; regression evals on every change are the monitoring of a
stochastic trajectory, not assertions on a deterministic function.

### Instrumentation is the debugger

Agent traces (which tool, what arguments, what returned, what the model said next) are the
narrated trace panel and anatomy strip of production systems. Breakpoints can't show why a
model chose a tool, the same way they can't show why a Q-value moved. Reading trajectories
is the skill in both worlds.

### The precise refinement

In agent work the *inner* loop (gradient descent on weights) already ran — at the lab,
before you got the model. You live entirely in outer loops:

- context and prompts shape behavior per-request (in-context; no weights change)
- your evals shape your *system* across iterations — selection-by-score over prompts, tools,
  and pipelines instead of over parameters

Fine-tuning / RLHF re-enters the inner loop; nothing conceptually new is required.

### The compact worldview for AI-native engineering

> **Write the score with the care you used to reserve for the code, expect the system to
> exploit every gap in it, measure distributions not runs, and build the instruments before
> you trust anything.**

Your evals are the most load-bearing code you write.
