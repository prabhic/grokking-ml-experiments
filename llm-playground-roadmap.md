# LLM playground roadmap

Build small playgrounds that each expose one hidden mechanism and let you manipulate it directly.

| # | Playground | What you manipulate | What it teaches | Why it is useful |
| -: | --- | --- | --- | --- |
| 0 | [Wave Frequency & Phase Playground](wave-frequency-phase-playground.html) | Amplitude, frequency, phase, time | How a simple wave carries changing values | Establishes the signal intuition behind sine/cosine positional encodings |
| 1 | Vector Similarity Playground | Two vectors, angle, length | Dot product, cosine similarity | Establishes the basic language of embeddings |
| 2 | Word Embedding Playground | Words such as `cat`, `dog`, `car` | Words → vectors → geometric relationships | Connects abstract vectors to semantic meaning |
| 3 | Embedding Dimensions Playground | Individual vector dimensions | Why one word is represented by many numbers | Removes the mystery around “768-dimensional embedding” |
| 4 | [Tokenization Playground](tokenization-lab.html) | Type text and inspect tokens | Text → tokens → token IDs | Shows what the LLM actually receives |
| 5 | [Token Embedding Lookup Playground](token-embedding-lookup-lab.html) | Token ID and embedding table | Token ID → embedding vector | Connects tokenization to vectors |
| 6 | [Positional Encoding Playground](positional-encoding-lab.html) | Token position, sequence length | How order enters the model | Explains why `dog bites man` differs from `man bites dog` |
| 7 | [Query–Key Similarity Playground](query-key-similarity-lab.html) | Query vector and several key vectors | Attention scoring | Shows how a token decides what to look at |
| 8 | [Softmax Playground](softmax-lab.html) | Raw attention scores / temperature | Scores → probabilities | Makes normalization and competition visible |
| 9 | [Single-Head Attention Playground](single-head-attention-lab.html) | Q, K, V vectors | `QKᵀ → softmax → weighted V` | Probably the single most important transformer playground |
| 10 | [Attention Sentence Playground](attention-sentence-lab.html) | A short sentence and one selected token | Which earlier tokens receive attention | Connects matrix math to language behavior |
| 11 | [Multi-Head Attention Playground](multi-head-attention-lab.html) | Several attention heads | Different heads focusing on different relationships | Explains why multiple heads exist |
| 12 | [Residual Connection Playground](residual-connection-lab.html) | Original vector + transformation | `x + f(x)` | Shows how information survives many layers |
| 13 | [Layer Normalization Playground](layer-normalization-lab.html) | Vector values before/after normalization | Mean, variance, scaling | Explains model stability without making it feel magical |
| 14 | [Feed-Forward Network Playground](feed-forward-network-lab.html) | Input vector, weights, activation | Linear → nonlinear → linear transformation | Shows what happens after attention |
| 15 | [Transformer Block Playground](transformer-block-lab.html) | Toggle attention, FFN, residuals, norm | One complete transformer layer | Integrates the previous concepts |
| 16 | [Next-Token Prediction Playground](next-token-prediction-lab.html) | Vocabulary logits | Hidden state → next-token scores | Connects transformer output to actual generation |
| 17 | [Logits → Softmax Playground](logits-softmax-lab.html) | Logits, temperature | Scores → token probabilities | Makes temperature intuitive |
| 18 | [Sampling Playground](sampling-lab.html) | Temperature, top-k, top-p | Deterministic vs creative generation | Explains why the same model produces different answers |
| 19 | [Context Window Playground](context-window-lab.html) | Add/remove earlier tokens | What the model can currently “see” | Clarifies context vs memory |
| 20 | [Causal Mask Playground](causal-mask-lab.html) | Reveal/mask future tokens | Why GPT cannot look ahead during training | Explains autoregressive prediction |
| 21 | [Loss Playground](loss-lab.html) | Predicted probability of correct token | Cross-entropy loss | Shows what “wrong prediction” mathematically means |
| 22 | [Gradient Descent Playground](gradient-descent-lab.html) | Weight, learning rate, loss surface | How weights improve | Connects prediction error to learning |
| 23 | [Single-Neuron Training Playground](single-neuron-training-lab.html) | One weight and bias | Forward pass → loss → gradient → update | Best first-principles entrance into training |
| 24 | [Tiny Language Model Training Playground](tiny-language-model-training-lab.html) | A tiny corpus like `I like tea` | Repeated next-token learning | Shows training as accumulation of statistical structure |
| 25 | [Backpropagation Playground](backpropagation-lab.html) | Tiny computation graph | How error flows backward | Demystifies gradient propagation |
| 26 | [Model Parameters Playground](model-parameters-lab.html) | Matrix dimensions, layer count | Where billions of parameters come from | Makes “7B model” tangible |
| 27 | [KV Cache Playground](kv-cache-lab.html) | Generate tokens one by one | Reusing previous keys and values | Explains why generation becomes efficient |
| 28 | [Prompt Context Playground](prompt-context-lab.html) | System/user/history messages | How the prompt becomes one sequence | Clarifies what the model actually sees |
| 29 | [RAG Similarity Playground](rag-similarity-lab.html) | Query/document embeddings | Retrieval by semantic similarity | Connects your cosine playground directly to RAG |
| 30 | [Chunking Playground](chunking-lab.html) | Chunk size and overlap | Documents → retrievable pieces | Shows why RAG quality depends on chunking |
| 31 | [Semantic Retrieval Playground](semantic-retrieval-lab.html) | Query and several chunks | Cosine scores and ranking | Makes retrieval failures visible |
| 32 | [Fine-Tuning Playground](fine-tuning-lab.html) | Before/after examples | How training changes behavior | Separates prompting from modifying weights |
| 33 | [LoRA Playground](lora-lab.html) | Base matrix + low-rank matrices | Small adapters modifying a large model | Makes parameter-efficient tuning intuitive |
| 34 | [RLHF / Preference Playground](rlhf-preference-lab.html) | Two candidate answers and a preference | Reward signals shaping behavior | Explains post-training conceptually |
| 35 | [Hallucination Playground](hallucination-lab.html) | Confidence vs available evidence | Prediction is not factual lookup | Critical mental model for using LLMs correctly |

## First-principles staircase

Text → Token → Token ID → Embedding vector → Similarity → Position → Attention → Softmax → Value mixing → Transformer block → Hidden representation → Logits → Next-token probability → Sampling → Generated text

### Learning

Prediction → Error → Loss → Gradient → Weight update → Repetition → Learned model

### LLM + external knowledge

Query embedding → Chunk embedding → Cosine similarity → Retrieval → Context injection → Generation

## Highest-value first ten

1. Tokenization
2. Embedding lookup
3. Vector/cosine similarity — [built](cosine-similarity-lab.html)
4. Positional encoding
5. Query–Key similarity
6. Softmax
7. Single-head attention
8. Full transformer block
9. Logits + next-token prediction
10. Gradient-descent training

## Build progress

- #0: [Wave Frequency & Phase Playground](wave-frequency-phase-playground.html)
- #1: [Vector Similarity Playground](cosine-similarity-lab.html)
- #2: [Word Embedding Playground](word-embedding-lab.html)
- #3: [Embedding Dimensions Playground](embedding-dimensions-lab.html)
- #3A: [Feature vs Embedding Vector Playground](feature-vs-embedding-lab.html)
- #3B: [Embedding Value Scale Playground](embedding-scale-lab.html)
- #4: [Tokenization Playground](tokenization-lab.html)
- #5: [Token Embedding Lookup Playground](token-embedding-lookup-lab.html)
- #6: [Positional Encoding Playground](positional-encoding-lab.html)
- #6-bridge: [Position Index → Vector Playground](position-index-to-vector-lab.html)
- #6A: [Learned Positional Embedding Playground](learned-positional-embedding-lab.html)
- #6B: [Rotary Position Encoding Playground](rotary-position-encoding-lab.html)
- #6C: [Sinusoidal Position Encoding Playground](sinusoidal-position-encoding-lab.html)
- #6C-bridge: [Waves and Position Playground](waves-and-position-lab.html)
- #6C0: [Number → Circle Playground](number-to-circle-lab.html)
- #7: [Query–Key Similarity Playground](query-key-similarity-lab.html)
- #8–#35: [Softmax through Hallucination Playgrounds](softmax-lab.html) — all remaining roadmap mechanisms are now available as standalone interactive labs.

The table order and the suggested first-ten learning order are distinct. Implementation follows the table; next is #4, tokenization.
