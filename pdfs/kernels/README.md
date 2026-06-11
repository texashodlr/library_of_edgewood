# Kernel Daily Digest — June 11, 2026

Collection of 20 arXiv papers covering GPU/AI accelerator architecture, LLM inference optimization, and memory systems.

## Papers

| ID | Title | Area |
|----|-------|------|
| [2604.15379v1](./2604.15379v1) | Fleet: Hierarchical Task-based Abstraction for Megakernels on Multi-Die GPUs | AMD GPU |
| [2605.03208v2](./2605.03208v2) | Kerncap: Automated Kernel Extraction and Isolation for AMD GPUs | AMD GPU |
| [2605.14718v1](./2605.14718v1) | Adapting AlphaEvolve to Optimize Fully Homomorphic Encryption on TPUs | TPU |
| [2605.17707v1](./2605.17707v1) | Speed Kills: Exploring Confused Deputy Attacks Through Edge AI Accelerators | Security |
| [2605.19481v1](./2605.19481v1) | C2CServe: Leveraging NVLink-C2C for Elastic Serverless LLM Serving on MIG | NVIDIA |
| [2605.27963v1](./2605.27963v1) | Throughput-Optimized Networks at Scale | Networking |
| [2605.30571v1](./2605.30571v1) | Memory-Bound but Not Bandwidth-Limited: The Physical AI Inference Gap | Memory |
| [2606.05080v1](./2606.05080v1) | AutoLab: Can Frontier Models Solve Long-Horizon Auto Research and Engineering Tasks? | AI Research |
| [2606.05495v1](./2606.05495v1) | SET: Stream-Event-Triggered Scheduling for Efficient CUDA Graph Pipelines | CUDA |
| [2606.05741v1](./2606.05741v1) | Space-CIM: Enabling Compute-In-Memory Accelerators for Thermally-Constrained Space Platforms | Space/Edge |
| [2606.06063v1](./2606.06063v1) | LLM-Based Porting of Optimized C++ to CUDA Through Deoptimization and Reoptimization | HPC |
| [2606.06910v1](./2606.06910v1) | Communication Strategy Selection for Multi-GPU 3D FDTD | Multi-GPU |
| [2606.08761v1](./2606.08761v1) | APEX4: Efficient Pure W4A4 LLM Inference via Intra-SM Compute Rebalancing | Quantization |
| [2606.09200v1](./2606.09200v1) | Resource-aware Computation-Communication Overlap for multi-GPU ML Workloads | Training |
| [2606.09937v1](./2606.09937v1) | RKSC: Reasoning-Aware KV Cache Sharing and Confident Early Exit | Inference |
| [2606.10435v1](./2606.10435v1) | Parallel Causal Associative Fields: Gated Sparse Memory for Long-Context Language Modeling | Memory |
| [2606.10671v1](./2606.10671v1) | FadeMem: Distance-Aware Memory Consolidation for Autoregressive Video Diffusion | Video AI |
| [2606.10944v1](./2606.10944v1) | Express Language Modeling | Attention |
| [2606.11145v1](./2606.11145v1) | OpenPCC: Open and Confidential LLM Serving on Commodity TEEs | Security |
| [2606.11164v1](./2606.11164v1) | ReasonAlloc: Hierarchical Decoding-Time KV Cache Budget Allocation for Reasoning Models | Inference |

## Highlights

- **Kerncap** (2605.03208) — AMD kernel extraction tool for iterative tuning. Directly applicable to MI300 work.
- **ReasonAlloc** (2606.11164) — KV cache allocation for reasoning models (o1/r1 style). Very timely given the reasoning model wave.
- **APEX4** (2606.08761) — First systematic study of W4A4 INT4 Tensor Core utilization. Fixes group dequantization overhead on CUDA cores.
- **Physical AI inference gap** (2605.30571) — Analyzes single-stream batch-1 decode vs batched cloud serving. Directly relevant to edge/robotics workloads.
- **Fleet** (2604.15379) — Addresses chiplet-based GPU designs (like MI300X) where CUDA/HIP expose flat exec model but hardware has private cache hierarchies.

## Quick Access

```bash
# List all PDFs
ls -la *.pdf | awk '{print $9, $5}'

# Total size
du -sh .
```

## Categories

- **GPU Architecture**: 2604.15379, 2605.03208, 2606.05495
- **LLM Inference**: 2606.08761, 2606.09937, 2606.11145, 2606.11164
- **Memory/KV Cache**: 2605.30571, 2606.10435, 2606.10671, 2606.10944
- **Multi-GPU/Training**: 2605.19481, 2606.06910, 2606.09200
- **Security**: 2605.17707, 2606.11145
- **Networking**: 2605.27963
- **Emerging/Research**: 2605.14718, 2605.27963, 2606.05080, 2606.05741, 2606.06063