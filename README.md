# Hi, I'm Edip

I build ML infrastructure from first principles — no ML libraries, no frameworks,
no dependencies. Just Rust and CUDA.

### 🔨 StonefishAI

A language model written entirely from scratch: hand-written autograd, byte-level
BPE, a RoPE/RMSNorm/SwiGLU transformer, our own CUDA driver FFI and cuBLAS
bindings. Trained on 2B tokens on a single consumer GPU.

| | |
|---|---|
| Dependencies | `cargo tree` → **1 line** |
| Tests | **71** (29 numerical gradient checks) |
| Model | **222M parameters**, 2B tokens, BPE-16k |
| Speed | **244k tok/s** (small model), **1.8× PyTorch** on the same GPU |
| Code | ~7,500 lines of Rust + 390 lines of CUDA kernels |

```console
$ cargo run --release -- demo 90
# trains a small GPT from scratch and writes Shakespeare in 90 seconds
```

[→ Repository](https://github.com/Edipcm-hash/stonefish) · [→ Turkish docs](https://github.com/Edipcm-hash/stonefish/blob/main/README-Tr.md)

### What I'm working on next

- `bf16` mixed precision + gradient checkpointing for a ~400M model
- A from-scratch Turkish language model with a browser demo
- Image-conditioned generation (small ViT encoder → the existing GPT)

### Currently

📍 İzmir, Turkey
