# Hi, I'm Edip

I have been writing code for **fourteen years**. No computer-science degree, no
bootcamp, no mentor — just a lot of broken builds, a lot of reading other people's
source code, and the stubborn habit of not moving on until I understand why
something works.

I am not a researcher. I am a programmer who likes to know what is underneath.

---

## The long way here

My first programs were bad, and I did not know they were bad. For years I measured
progress by "it runs" — which, I have since learned, is the least interesting
question you can ask about software.

The turning point was not a language or a framework. It was learning to **read the
output** instead of trusting that the program had done what I meant. Then learning
to measure instead of guessing. Then learning that "it works on my machine" is not a
claim, it is an apology.

Fourteen years later I still get things wrong. The difference is that now I find out
sooner, and I write down what I found.

## What I believe about code

- **Read the output.** A green check mark is not evidence; the printed number is.
- **Measure before you optimise.** My best guess about where time goes is wrong
  surprisingly often.
- **Fewer dependencies is a feature.** Every one you add is code you did not write,
  cannot fix, and will still be debugging in five years.
- **If you cannot explain it, you do not understand it.** This is why I write things
  down — for the reader, but mostly to find out whether I actually know.
- **The honest number is worth more than the impressive one.** A small true result
  survives scrutiny; a big vague one does not.

## What I work on now

Low-level systems work in **Rust** and **CUDA**: performance, memory layout, and the
unglamorous layers that everything else is built on. Lately that has meant machine
learning — not by calling a framework, but by building the pieces a framework would
have given me.

---

## The masterwork: StonefishAI

If I had to point at one thing and say *this is what fourteen years added up to*, it
would be this.

A language model written **entirely from scratch**, with **zero dependencies**:
hand-written autograd, a byte-level BPE tokenizer, a RoPE/RMSNorm/SwiGLU transformer,
our own CUDA driver FFI, cuBLAS and NVRTC bindings — and a 222M-parameter model
trained on 2.05 billion tokens on a single consumer GPU. It took five months.

```console
$ cargo tree
stonefish_ai v1.0.0
```

That is the whole dependency tree. No `torch`, no `candle`, no `cudarc` — the CUDA
driver is loaded at runtime through the operating system's own loader.

| | |
|---|---|
| Parameters | **222,331,904** |
| Training data | **2,047,457,313 tokens** — TinyStories + Project Gutenberg, exactly one epoch |
| Dependencies | **0** |
| Tests | **75**, including 32 numerical gradient checks |
| Quality | **BPC 0.6064** on held-out data (random baseline 2.909) |
| PyTorch parity | same weights, same batches → loss differs by **1.8e-05** |
| Throughput | **10,772 tok/s** at 222M on one RTX 5070 |
| Code | 10,328 lines of Rust, 711 lines of CUDA, 1,415 lines of FFI |

```console
$ cargo run --release -- demo 90
# trains a small GPT from scratch and writes Shakespeare in 90 seconds
```

It is **not** a chat assistant, and the README says so in the first screen. It
continues English text; it does not answer questions, and it states invented facts
fluently. Being clear about that was part of the work.

[→ Repository](https://github.com/Edipcm-hash/stonefish) ·
[→ English README](https://github.com/Edipcm-hash/stonefish/blob/main/README-Eng.md) ·
[→ Turkish README](https://github.com/Edipcm-hash/stonefish/blob/main/README-Tr.md)

---

## What I'm working on next

- `bf16` mixed precision and gradient checkpointing — the honest path to a ~400M
  model on the same 12 GB card
- A from-scratch Turkish language model, with a browser demo
- Reading more source code than I write. Still the fastest way to learn.

## Elsewhere

📍 İzmir, Turkey

I am not on social media. If you want to reach me, open an issue — I read them.
