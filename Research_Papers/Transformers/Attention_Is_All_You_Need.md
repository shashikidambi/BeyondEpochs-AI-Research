# Attention Is All You Need (Vaswani et al., 2017)

**Paper:** [arXiv:1706.03762](https://arxiv.org/abs/1706.03762)  
**Authors:** Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Lukasz Kaiser, Illia Polosukhin  
**Published:** NIPS 2017

---

## 🔍 Summary

The **Transformer** architecture replaces recurrent and convolutional structures entirely with attention mechanisms, achieving faster training and superior performance in sequence transduction tasks such as neural machine translation.

It introduces:
- **Scaled dot-product attention**
- **Multi-head attention**
- **Positional encodings**
- Deep **encoder-decoder stacks** with residual connections and normalization

By eliminating recurrence, the Transformer enables **massive parallelization** and reduces sequence path lengths from O(n) to O(1).

---

## 🧠 Core Ideas

| Concept | Description |
|----------|--------------|
| **Self-Attention** | Computes attention within a sequence, allowing each token to attend to all others. |
| **Multi-Head Attention** | Runs attention in parallel “heads,” enabling the model to capture multiple representation subspaces. |
| **Positional Encoding** | Adds sequence order information using sinusoidal patterns (no recurrence). |
| **Feed-Forward Layers** | Position-wise linear projections applied to each token embedding. |
| **Residuals + LayerNorm** | Stabilizes training and improves gradient flow. |

---

## ⚙️ Architecture Overview

- **Encoder:** 6 identical layers each with Multi-Head Self-Attention and Feed-Forward sublayers.  
- **Decoder:** Similar structure, with additional Encoder-Decoder attention and masked self-attention.  
- **Attention Formula:**
  \[
  \text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V
  \]
- **Positional Encoding:**
  \[
  PE_{(pos,2i)} = \sin\left(\frac{pos}{10000^{2i/d_{model}}}\right),
  \quad
  PE_{(pos,2i+1)} = \cos\left(\frac{pos}{10000^{2i/d_{model}}}\right)
  \]

---

## 🚀 Results
- **Task:** English–German and English–French translation (WMT 2014).  
- **BLEU Score:** 28.4 (EN–DE), outperforming previous SOTA models.  
- **Training:** 3.5 days on 8 GPUs — much faster than RNN/CNN equivalents.

---

## 🌍 Impact
The Transformer became the foundation for:
- **BERT, GPT, T5, PaLM, LLaMA**
- **RAG pipelines** combining retrieval + generation
- **Agentic systems** (e.g., task-orchestrated LLM frameworks)
- **MCP architectures** (modular cognitive pipelines) that extend multi-head reasoning

---

## 🧪 Suggested Experiment
**Goal:** Train a miniature Transformer for language modeling.  
**Dataset:** [Tiny Shakespeare](https://github.com/karpathy/char-rnn/blob/master/data/tinyshakespeare/input.txt)  
**Steps:**
1. Tokenize dataset into character or word tokens.
