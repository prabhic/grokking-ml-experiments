# Grokking ML experiments

This repository has two deliberately separate tracks: experiments that follow
Luis Serrano's *Grokking Machine Learning*, and personal playgrounds built while
following the ideas onward into modern AI, ML, and LLMs.

Small, self-contained playgrounds (single HTML files, no build step, no dependencies) plus
notes written to build intuition for the ideas in each chapter. Open any `.html` file
directly in a browser. For a guided view, open [`index.html`](index.html): it groups the
Grokking Machine Learning experiments and LLM concept playgrounds in a collapsible explorer.

## Book-aligned experiments

| File | Chapter | What it is |
|---|---|---|
| [`grid-world-rl.html`](grid-world-rl.html) | 2 | Q-learning playground — a robot learns a grid board with treasure, dragon and step costs. Tune α / γ / ε, train in bulk or step through one episode, or drive the robot yourself. |
| [`linear-regression-lab.html`](linear-regression-lab.html) | 3 | Linear-regression playground — watch a line get nudged into the data with the square and absolute tricks, see the error surface ("Mount Errorest") side by side with the data, add an outlier and see what it does. |
| [`ml-mental-models.md`](ml-mental-models.md) | — | Notes on the mental-model shifts from software engineering to ML, and how the same worldview applies to building AI agents, applications and evals. |

## Personal learning playgrounds

Not part of the book's official chapter code. These are first-principles labs built
to make embeddings, transformer internals, generation, training, and retrieval
playable while learning them.

| File | What it is |
|---|---|
| [`cosine-similarity-lab.html`](cosine-similarity-lab.html) | Dot product & cosine similarity playground — drag two vector endpoints and watch the dot product, magnitudes, angle and cosine similarity update live. Presets for same direction / 90° apart / opposite. Shows why length changes the dot product but leaves cosine similarity at 1 — the reason embeddings are compared by angle, not by dot product. |
| [`wave-frequency-phase-playground.html`](wave-frequency-phase-playground.html) | Signal foundation playground — change amplitude, frequency, phase, and time to see how a wave carries a changing numeric value. This is the intuition underneath sine/cosine position signals. |

| Stage | Playgrounds | Focus |
|---|---|---|
| Signal foundations | [Wave frequency & phase](wave-frequency-phase-playground.html) · [Waves and position](waves-and-position-lab.html) · [Number → circle](number-to-circle-lab.html) | How changing numbers become signals and circle coordinates |
| Embeddings | [Cosine similarity](cosine-similarity-lab.html) · [Word embeddings](word-embedding-lab.html) · [Embedding dimensions](embedding-dimensions-lab.html) · [Features vs dimensions](feature-vs-embedding-lab.html) · [Embedding scale](embedding-scale-lab.html) | Words, vectors, dimensions, direction, magnitude |
| Tokens and positions | [Tokenization](tokenization-lab.html) · [Token lookup](token-embedding-lookup-lab.html) · [Position encoding](positional-encoding-lab.html) · [Index → vector](position-index-to-vector-lab.html) · [Learned positions](learned-positional-embedding-lab.html) · [Rotary positions](rotary-position-encoding-lab.html) · [Sinusoidal positions](sinusoidal-position-encoding-lab.html) | Text becomes ordered, position-aware vectors |
| Attention and blocks | [Query–key similarity](query-key-similarity-lab.html) · [Softmax](softmax-lab.html) · [Single-head attention](single-head-attention-lab.html) · [Attention sentence](attention-sentence-lab.html) · [Multi-head attention](multi-head-attention-lab.html) · [Residual connections](residual-connection-lab.html) · [Layer normalization](layer-normalization-lab.html) · [Activation function](activation-function-lab.html) · [Feed-forward network](feed-forward-network-lab.html) · [Transformer block](transformer-block-lab.html) | Tokens communicate, transform, and preserve information |
| Prediction and learning | [Next-token prediction](next-token-prediction-lab.html) · [Logits → softmax](logits-softmax-lab.html) · [Sampling](sampling-lab.html) · [Context window](context-window-lab.html) · [Causal mask](causal-mask-lab.html) · [Loss](loss-lab.html) · [Gradient descent](gradient-descent-lab.html) · [Single-neuron training](single-neuron-training-lab.html) · [Tiny language model](tiny-language-model-training-lab.html) · [Backpropagation](backpropagation-lab.html) · [Model parameters](model-parameters-lab.html) · [KV cache](kv-cache-lab.html) · [Prompt context](prompt-context-lab.html) | Scores become text; errors become learning |
| Retrieval and adaptation | [RAG similarity](rag-similarity-lab.html) · [Chunking](chunking-lab.html) · [Semantic retrieval](semantic-retrieval-lab.html) · [Fine-tuning](fine-tuning-lab.html) · [LoRA](lora-lab.html) · [RLHF / preference](rlhf-preference-lab.html) · [Hallucination](hallucination-lab.html) | External knowledge, behavior changes, and evidence |

## Note

The [LLM playground roadmap](llm-playground-roadmap.md) stores the 35 proposed experiments, the first-principles staircases, and the suggested first-ten learning order.

Only my own experiments live here. The book's official code repository is at
[github.com/luisguiserrano/manning](https://github.com/luisguiserrano/manning).
