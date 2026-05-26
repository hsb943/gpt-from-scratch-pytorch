# gpt-from-scratch-pytorch
Decoder-only GPT-style transformer implemented and trained from scratch in PyTorch on a technical distributed systems corpus.

# GPT-Style Decoder Transformer From Scratch in PyTorch

## 1. Project Overview

This project implements and trains a decoder-only GPT-style transformer from scratch using PyTorch.

The primary objective of this project was to deeply understand:

1. Autoregressive language modeling
2. Transformer internals
3. Self-attention mechanisms
4. Training dynamics of GPT-style architectures
5. How neural networks learn statistical language structure from raw text

Instead of training on generic text like Shakespeare, this model was trained on a technical distributed systems corpus derived from *Designing Data-Intensive Applications (DDIA)* to observe whether a small transformer could learn specialized technical vocabulary and document structure.

---

# 2. Key Features

## 2.1 Transformer Architecture

Implemented from scratch:

1. Token embeddings
2. Positional embeddings
3. Masked causal self-attention
4. Multi-head attention
5. Feed-forward neural networks
6. Residual connections
7. Layer normalization
8. Autoregressive text generation

---

## 2.2 Training Pipeline

Implemented manually without high-level training frameworks.

Includes:

1. Custom batching
2. Train/validation split
3. Loss estimation
4. AdamW optimizer
5. Sampling during training
6. Intermediate checkpoint text generation

---

## 2.3 Training Progression Tracking

The model automatically saves generated outputs at multiple training stages:

1. `sample_step_0.txt`
2. `sample_step_500.txt`
3. `sample_step_1000.txt`
4. `sample_step_2000.txt`
5. `sample_step_3000.txt`
6. `sample_step_4000.txt`
7. `sample_step_4999.txt`

This demonstrates how transformers gradually learn language structure from random noise.

---

# 3. Model Configuration

| Parameter | Value |
|---|---|
| Parameters | 10.84M |
| Framework | PyTorch |
| GPU | Google Colab T4 |
| Context Length | 256 |
| Embedding Dimension | 384 |
| Attention Heads | 6 |
| Transformer Layers | 6 |
| Dropout | 0.2 |
| Training Iterations | 5000 |
| Learning Rate | 3e-4 |

---

# 4. Dataset

The model was trained on extracted textual content from a technical distributed systems corpus inspired by DDIA.

The goal was to study whether a relatively small transformer trained from scratch could learn:

1. Technical vocabulary
2. Document formatting structure
3. Distributed systems terminology
4. Paragraph rhythm
5. Statistical language patterns

---

# 5. Project Structure

```text
gpt.py                  -> Transformer architecture + training loop
input.txt               -> Training corpus
more.txt                -> Final generated output
sample_step_*.txt       -> Intermediate generated outputs
README.md               -> Project documentation
```

---

# 6. Architecture Flow

```text
Input Text
    ↓
Character Encoding
    ↓
Token + Positional Embeddings
    ↓
Transformer Blocks
    ↓
Masked Self-Attention
    ↓
Feed Forward Layers
    ↓
Linear Projection
    ↓
Next Character Prediction
```

---

# 7. Training Results

## 7.1 Loss Reduction

Training successfully reduced loss from:

```text
step 0    -> train loss 4.82
step 4999 -> train loss 0.70
```

This demonstrates that the transformer successfully learned statistical language structure from the training corpus.

---

## 7.2 Example Generated Outputs

Examples of learned technical vocabulary:

```text
distributed storage engine
partitioning
schema
Avro
query
records
snapshot
serializable
message brokers
```

Example generated text:

```text
to the new device and the haltable (it online) process its actively becomes
time poliers whether snapshot. SSI will such us any up-to-mered serializable, but it’s
worth wise statement.

An OLTP: error A explicit is per a handling expressent, because there are many systems
duplicated, and aband thus fencing to change data changes...
```

---

# 8. What the Model Successfully Learned

The model demonstrated learning of:

1. Technical vocabulary
2. Database terminology
3. Distributed systems language patterns
4. Paragraph formatting
5. Bullet-point style structure
6. Technical writing rhythm
7. Statistical token relationships

Importantly, none of these concepts were manually programmed into the model.

The transformer learned these patterns directly from raw text through autoregressive next-character prediction.

---

# 9. Limitations

This project is educational and experimental in nature.

Current limitations include:

1. Character-level modeling
2. Lack of semantic reasoning
3. No factual consistency guarantees
4. Small training corpus
5. No pretrained initialization
6. No distributed training
7. No token-level BPE tokenizer

Because the model predicts characters instead of semantic tokens, generated text may contain partially coherent but nonsensical phrases.

Example:

```text
shared-deplay bag fit 0
```

This demonstrates the limitations of small character-level transformers trained from scratch.

---

# 10. Key Learnings

This project helped build practical understanding of:

1. Transformer internals
2. Causal self-attention
3. Positional embeddings
4. Autoregressive training
5. Training dynamics
6. Loss optimization
7. Context window limitations
8. GPU memory tradeoffs
9. Statistical language learning
10. Why scaling dramatically changes model capability

---

# 11. Future Improvements

Potential future improvements include:

1. Token-level BPE tokenizer
2. GPT-2 finetuning
3. Checkpoint saving/loading
4. Flash Attention
5. Distributed training
6. Mixed precision training
7. Larger technical corpora
8. vLLM inference serving
9. Multi-GPU experimentation
10. Kubernetes deployment

---

# 12. Final Takeaway

This project demonstrates that transformers are fundamentally statistical sequence learners.

Even a relatively small 10.84M parameter decoder-only transformer trained from scratch can learn meaningful technical vocabulary and document structure purely from raw text data.

The project serves as a foundational exploration into how modern GPT-style language models function internally.
