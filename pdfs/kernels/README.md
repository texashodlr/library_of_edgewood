# Kernels Directory

This directory contains papers related to GPU architecture, AI accelerator systems, LLM inference optimization, memory bandwidth, and high-performance computing kernels.

## Paper Reviews

---

### 1. Fleet: Hierarchical Task-based Abstraction for Megakernels on Multi-Die GPUs

**Source:** arXiv 2604.15379v1 (April 2026)  
**Authors:** Sangeeta Chowdhary, Ryan Swann, Sean Siddens, et al. (AMD Research)  
**File:** `2604.15379v1`

#### Summary

Modern GPUs adopt chiplet-based designs with multiple private cache hierarchies, but current programming models (CUDA/HIP) expose a flat execution hierarchy that cannot express chiplet-level locality or synchronization. This mismatch leads to redundant data movement and underutilization of memory bandwidth. Fleet introduces a hierarchical task-based abstraction that maps megakernels onto multi-die GPU architectures, enabling developers to express locality and synchronization at the chiplet level.

#### Key Findings
1. **Chiplet mismatch** — CUDA/HIP expose flat execution model but MI300X has private cache hierarchies per chiplet
2. **Fleet abstraction** — New programming model for expressing hierarchical locality and synchronization
3. **Memory bandwidth optimization** — Reduces redundant data movement across chiplet boundaries
4. **AMD MI300X focus** — Directly applicable to your MI300X workloads on asrock

#### Actionable Next Steps
- [ ] Review Fleet abstraction for potential integration with HIP kernels on MI300X
- [ ] Evaluate whether hierarchical scheduling could improve your multi-GPU workloads
- [ ] Consider how chiplet-level locality could reduce memory bandwidth pressure

---

### 2. Kerncap: Automated Kernel Extraction and Isolation for AMD GPUs

**Source:** arXiv 2605.03208v2 (May 2026)  
**Authors:** AMD Research  
**File:** `2605.03208v2`

#### Summary

Iterative GPU kernel tuning is bottlenecked by the scale of the applications that host the kernels. Rapid iteration requires isolating the kernel so it can be edited, recompiled, and validated without rebuilding the full application—but manual isolation is time-consuming and error-prone. Kerncap automates kernel extraction and isolation for AMD GPUs, enabling rapid iterative tuning workflows.

#### Key Findings
1. **Automated extraction** — Kernel isolation without manual refactoring
2. **Rapid iteration** — Edit-compile-validate cycle without full application rebuilds
3. **AMD GPU focus** — Built specifically for AMD GPU workflows
4. **Directly applicable** — Very relevant for your MI300 kernel optimization work

#### Actionable Next Steps
- [ ] Evaluate Kerncap for your AMD MI300X kernel development workflow
- [ ] Use for iterative performance tuning on asrock
- [ ] Reduce kernel development cycle time

---

### 3. Adapting AlphaEvolve to Optimize Fully Homomorphic Encryption on TPUs

**Source:** arXiv 2605.14718v1 (May 2026)  
**Authors:** Google  
**File:** `2605.14718v1`

#### Summary

The deployment of Fully Homomorphic Encryption (FHE) at scale is hindered due to its heavy computational overhead. While specialized hardware accelerators like Google TPUs can help, mapping complex cryptographic kernels onto such architectures remains a challenge. This paper adapts AlphaEvolve (Google's AI-driven discovery system) to optimize FHE kernels on TPUs, co-optimizing between the systolic array-based MXU and VPUs.

#### Key Findings
1. **FHE compute bottleneck** — Heavy computational overhead limits FHE deployment at scale
2. **TPU optimization** — Co-optimization of MXU (systolic array) and VPU (vector) execution
3. **AlphaEvolve adaptation** — AI-driven discovery applied to cryptographic kernels
4. **Jaxite backend** — Google's FHE backend targeting TPUs and GPUs

#### Actionable Next Steps
- [ ] Consider FHE as a future workload for TPU infrastructure
- [ ] Review Jaxite for potential GPU-based FHE experiments
- [ ] Track AlphaEvolve applications to other HPC domains

---

### 4. Speed Kills: Exploring Confused Deputy Attacks Through Edge AI Accelerators

**Source:** arXiv 2605.17707v1 (May 2026)  
**Authors:** Various  
**File:** `2605.17707v1`

#### Summary

AI Accelerators (AIAs) like TPUs are specialized hardware enabling optimal and efficient AI execution on edge devices. Unlike applications, AIAs are not bound by OS restrictions and have limited visibility into application processor security mechanisms. This paper explores Confused Deputy Attacks (CDA) on edge AIAs, where a malicious user can cause the AIA to access memory regions it shouldn't have access to.

#### Key Findings
1. **Security gap** — AIAs lack OS-level security boundaries that CPUs/AP have
2. **SMID vulnerability** — System Memory ID validation failures enable attacks
3. **Black-box challenge** — AIA ISA is proprietary, limiting security analysis
4. **Attack surface** — Edge AI deployments may be vulnerable to memory access attacks

#### Actionable Next Steps
- [ ] Audit your edge AI deployments for similar security gaps
- [ ] Review SMID validation in your AI accelerator firmware
- [ ] Consider security implications for multi-tenant AI serving

---

### 5. C2CServe: Leveraging NVLink-C2C for Elastic Serverless LLM Serving on MIG

**Source:** arXiv 2605.19481v1 (May 2026)  
**Authors:** NVIDIA  
**File:** `2605.19481v1`

#### Summary

Modern LLM serving is increasingly serverless with large model catalogs, long-tail invocations, and multi-tenant demand. Existing GPU serving systems face a tradeoff: dedicated-GPU allocation wastes scarce HBM under sparse traffic, while GPU time-sharing places model initialization on the cold-start path. Spatial GPU sharing like MIG provides isolation but each slice has too little HBM for modern LLM weights. C2CServe leverages NVLink-C2C to enable elastic serverless LLM serving on MIG partitions.

#### Key Findings
1. **Serverless LLM challenge** — Cold start time from weight loading hurts latency
2. **NVLink-C2C** — Enables memory sharing between MIG partitions
3. **Elastic serving** — Dynamically allocate HBM across model instances
4. **HBM efficiency** — More efficient utilization of scarce GPU memory

#### Actionable Next Steps
- [ ] Evaluate MIG partitions for multi-tenant LLM serving
- [ ] Consider NVLink-C2C for memory sharing in multi-GPU inference
- [ ] Review cold-start optimization strategies for your serving infrastructure

---

### 6. Throughput-Optimized Networks at Scale

**Source:** arXiv 2605.27963v1 (May 2026)  
**Authors:** Meta, Google, NVIDIA  
**File:** `2605.27963v1`

#### Summary

Datacenter network design plays a critical role in AI training by supporting scaling to thousands of accelerators. An open problem—designing a near-optimal throughput-oriented network (topology, routing, and collectives)—has not been achieved at scale with broad applicability to physical constraints. This paper addresses this with a compelling use-case: Google's TPU v4/5p supercomputer where topology can be reconfigured for higher all-to-all throughput.

#### Key Findings
1. **Network topology matters** — Critical for scaling to thousands of accelerators
2. **All-to-all collectives** — Major bottleneck in large-scale training
3. **TPU v4/5p architecture** — Reconfigurable topology for optimal throughput
4. **Physical constraints** — Practical considerations for datacenter deployment

#### Actionable Next Steps
- [ ] Review network topology design for your multi-GPU clusters
- [ ] Analyze all-to-all collective performance in training workloads
- [ ] Consider topology-aware job scheduling

---

### 7. Memory-Bound but Not Bandwidth-Limited: The Physical AI Inference Gap in Batch-1 LLM Decode

**Source:** arXiv 2605.30571v1 (May 2026)  
**Authors:** Stanford  
**File:** `2605.30571v1`

#### Summary

Physical AI systems (robots, autonomous vehicles, embodied agents) often run single-stream batch-1 autoregressive decode, where one robot or user session waits for the next token. This workload is typically described as memory-bandwidth-bound—each decode step streams model weights and KV cache, so latency should scale with peak HBM bandwidth. This paper shows this account is true but incomplete: there's a significant gap between theoretical bandwidth and actual inference performance.

#### Key Findings
1. **Batch-1 decode gap** — Memory-bound but not bandwidth-limited in practice
2. **Physical AI workload** — Different from cloud batched serving
3. **Latency analysis** — Gap between theoretical and actual performance
4. **Optimization opportunity** — Direct relevance to edge/robotics inference

#### Actionable Next Steps
- [ ] Profile your edge inference workloads for similar gaps
- [ ] Consider optimized decode kernels for batch-1 scenarios
- [ ] Evaluate KV cache optimization specifically for physical AI use cases

---

### 8. AutoLab: Can Frontier Models Solve Long-Horizon Auto Research and Engineering Tasks?

**Source:** arXiv 2606.05080v1 (June 2026)  
**Authors:** Google DeepMind  
**File:** `2606.05080v1`

#### Summary

Scientific and engineering progress is fundamentally a long-horizon iterative process: proposing changes, running experiments, measuring outcomes, and continuously refining artifacts. Yet existing benchmarks for frontier models primarily evaluate either single-turn responses or short-horizon agent trajectories, failing to capture the challenges of sustained iterative improvement. AutoLab is a new benchmark for ultra long-horizon closed-loop automation in research and engineering tasks.

#### Key Findings
1. **Benchmark gap** — Existing benchmarks don't capture iterative engineering
2. **Long-horizon tasks** — Multi-step research and engineering workflows
3. **Frontier model evaluation** — Tests GPT-4o, Claude, Gemini on sustained tasks
4. **System optimization** — Measures performance improvement over baselines

#### Actionable Next Steps
- [ ] Consider AutoLab-like evaluation for your AI infrastructure automation
- [ ] Track frontier model capabilities for engineering automation
- [ ] Evaluate multi-turn agent workflows for operational tasks

---

### 9. SET: Stream-Event-Triggered Scheduling for Efficient CUDA Graph Pipelines

**Source:** arXiv 2606.05495v1 (June 2026)  
**Authors:** NVIDIA  
**File:** `2606.05495v1`

#### Summary

Achieving peak GPU performance remains a significant challenge as system throughput is constrained by host-device synchronization delays and kernel scheduling overheads, even with aggressive kernel optimizations and batch processing. Furthermore, existing approaches often underutilize hardware resources such as compute cores and copy engines due to scheduling overheads. SET proposes a CUDA runtime framework for task-parallel pipelines to minimize synchronization and maximize hardware utilization.

#### Key Findings
1. **Scheduling bottleneck** — Host-device sync delays limit GPU throughput
2. **Stream-event triggered** — New scheduling paradigm for CUDA graphs
3. **Resource utilization** — Better use of compute cores and copy engines
4. **Task-parallel pipelines** — Framework for overlapping execution

#### Actionable Next Steps
- [ ] Evaluate SET scheduling for your CUDA workloads
- [ ] Profile your current kernel scheduling overhead
- [ ] Consider stream-event patterns for overlapping compute and communication

---

### 10. Space-CIM: Enabling Compute-In-Memory Accelerators for Thermally-Constrained Space Platforms

**Source:** arXiv 2606.05741v1 (June 2026)  
**Authors:** Various  
**File:** `2606.05741v1`

#### Summary

The rapid growth in AI compute demand has driven a massive surge in data center construction, precipitating an energy and sustainability crisis. Motivated by abundant solar energy in outer space and reduced launch costs, orbital data centers are emerging as a potential pathway for future AI compute scaling. While the cold background in vacuum seems appealing for cooling, computing systems operating in space face unique thermal challenges. Space-CIM explores compute-in-memory accelerators for thermally-constrained space platforms.

#### Key Findings
1. **Orbital datacenters** — Space-based AI compute as future scaling path
2. **Compute-In-Memory** — CIM for thermally constrained environments
3. **Thermal challenges** — Space has unique cooling constraints despite cold background
4. **CIM optimization** — CiMLoop modeling tool for CIM design

#### Actionable Next Steps
- [ ] Track orbital datacenter developments for future infrastructure planning
- [ ] Review CIM architecture for edge deployment efficiency
- [ ] Consider thermal-aware compute placement

---

### 11. LLM-Based Porting of Optimized C++ to CUDA Through Deoptimization and Reoptimization

**Source:** arXiv 2606.06063v1 (June 2026)  
**Authors:** Microsoft  
**File:** `2606.06063v1`

#### Summary

When porting high-performance computing (HPC) code from CPU to GPU, CPU-oriented optimizations may obstruct LLM-based CUDA translation. This paper designs and evaluates a Deopt-Reopt workflow that first simplifies the input C++ code and then retranslates and reoptimizes it for CUDA. Evaluated on twelve HPC kernels with two LLMs (gpt-oss-120b and qwen-3-235b) in single-shot and iterative settings.

#### Key Findings
1. **Deopt-Reopt workflow** — Simplify CPU code before GPU translation
2. **12 HPC kernels** — Tested on GEMM, Conv2D, FFT, stencil computations
3. **LLM translation** — gpt-oss-120b and qwen-3-235b evaluated
4. **Single-shot vs iterative** — Iterative refinement improves results

#### Actionable Next Steps
- [ ] Consider Deopt-Reopt for HPC code porting projects
- [ ] Evaluate LLM-based code translation for your CUDA kernels
- [ ] Use iterative refinement for complex kernel porting

---

### 12. Communication Strategy Selection for Multi-GPU 3D FDTD

**Source:** arXiv 2606.06910v1 (June 2026)  
**Authors:** Various  
**File:** `2606.06910v1`

#### Summary

This paper describes a communication-strategy study for multi-GPU three-dimensional finite-difference time-domain computation with convolutional perfectly matched layer boundary conditions using CUDA. Metrics include runtime, throughput, strong-scaling efficiency, CPML overhead, host-staged vs direct GPU-to-GPU exchange speedup, and enlarged-ghost speedup.

#### Key Findings
1. **Multi-GPU communication** — Host-staged vs direct GPU-to-GPU exchange
2. **3D FDTD with CPML** — Specific domain but generalizable insights
3. **Strong scaling** — Efficiency analysis across GPU counts
4. **Ghost region strategies** — Trade-offs in halo exchange approaches

#### Actionable Next Steps
- [ ] Profile communication strategies in your multi-GPU workloads
- [ ] Compare host-staged vs direct GPU-to-GPU for your patterns
- [ ] Evaluate optimal halo exchange strategies

---

### 13. APEX4: Efficient Pure W4A4 LLM Inference via Intra-SM Compute Rebalancing

**Source:** arXiv 2606.08761v1 (June 2026)  
**Authors:** NVIDIA  
**File:** `2606.08761v1`

#### Summary

W4A4 quantization promises full utilization of INT4 Tensor Cores, yet group dequantization overhead on CUDA Cores has driven existing systems to mixed-precision fallbacks. This paper presents the first systematic study of how intra-SM compute balance governs this bottleneck. Through controlled benchmarks across four GPUs from Ampere and Ada architectures, they identify the Tensor Cores to CUDA Cores throughput ratio (ρ) as the primary hardware indicator.

#### Key Findings
1. **W4A4 bottleneck** — Group dequantization overhead limits INT4 Tensor Core utilization
2. **Intra-SM compute balance** — ρ ratio governs performance
3. **2.0-2.5× speedup** — On GPUs with favorable ρ ratios
4. **First systematic study** — Comprehensive analysis of W4A4 on NVIDIA GPUs

#### Actionable Next Steps
- [ ] Evaluate W4A4 quantization for your inference workloads
- [ ] Consider GPU architecture when selecting quantization formats
- [ ] Profile intra-SM balance for your specific GPU models

---

### 14. Resource-aware Computation-Communication Overlap for Multi-GPU ML Workloads

**Source:** arXiv 2606.09200v1 (June 2026)  
**Authors:** Meta  
**File:** `2606.09200v1`

#### Summary

The rapid growth of large-scale ML has made distributed training across multiple GPUs a fundamental component of modern ML systems. As model sizes and computational throughput continue to increase, communication overhead has become a dominant bottleneck in multi-GPU training, particularly when computation and communication are executed sequentially. This work explores concurrent execution of computation and collective communication using portable runtime control.

#### Key Findings
1. **Comm overhead bottleneck** — Dominant in large-scale multi-GPU training
2. **Concurrent execution** — Overlap compute and communication
3. **Portable runtime** — Works across different GPU systems
4. **Meta research** — Practical implications for training infrastructure

#### Actionable Next Steps
- [ ] Profile compute-communication overlap in your training workloads
- [ ] Implement overlapped collectives for multi-GPU training
- [ ] Consider portable runtimes for cross-platform training

---

### 15. RKSC: Reasoning-Aware KV Cache Sharing and Confident Early Exit

**Source:** arXiv 2606.09937v1 (June 2026)  
**Authors:** Various  
**File:** `2606.09937v1`

#### Summary

RKSC (Reasoning-Aware KV Cache Sharing) is a training-free inference framework that eliminates two structural redundancies in multi-branch LLM reasoning pipelines. ASKS computes the prefix KV cache once and broadcasts it to all semantically similar branches via hidden-state cosine similarity. CGEE applies two complementary exit mechanisms for early termination in reasoning chains.

#### Key Findings
1. **KV cache sharing** — Prefix caching for reasoning branches
2. **Semantic similarity** — Hidden-state cosine similarity for branch matching
3. **Early exit** — CGEE for confident early termination
4. **vLLM/SGLang extension** — Builds on existing prefix caching

#### Actionable Next Steps
- [ ] Evaluate RKSC for your multi-branch inference workloads
- [ ] Consider KV cache sharing for reasoning models (o1/r1 style)
- [ ] Implement early exit for confident reasoning paths

---

### 16. Parallel Causal Associative Fields: Gated Sparse Memory for Long-Context Language Modeling

**Source:** arXiv 2606.10435v1 (June 2026)  
**Authors:** Meta  
**File:** `2606.10435v1`

#### Summary

Transformers achieve strong language modeling performance via direct token-to-token communication, but causal self-attention scales quadratically with context length. Recurrent and state-space models reduce this cost but compress history into fixed-size states. This paper studies a third primitive: parallel content-addressed memory over causal successor records. PCAF writes local records from a context window and enables efficient long-context modeling.

#### Key Findings
1. **Alternative to attention** — Content-addressed memory vs quadratic attention
2. **Parallel causal records** — New primitive for long-context modeling
3. **Fixed memory size** — Avoids quadratic scaling
4. **Meta research** — Practical approach to long-context challenges

#### Actionable Next Steps
- [ ] Consider PCAF for very long context workloads
- [ ] Evaluate memory vs attention trade-offs for your use cases
- [ ] Track alternative attention approaches for long-context

---

### 17. FadeMem: Distance-Aware Memory Consolidation for Autoregressive Video Diffusion

**Source:** arXiv 2606.10671v1 (June 2026)  
**Authors:** ByteDance  
**File:** `2606.10671v1`

#### Summary

Autoregressive video generators synthesize long videos by generating successive temporal segments, but their historical KV cache grows with video length. Existing bounded-cache methods reduce this cost with local windows, sink tokens, or compressed memory states, but they assign fixed roles to different history parts. FadeMem proposes distance-aware KV memory consolidation that organizes historical KV blocks into a temporal hierarchy under a fixed cache budget.

#### Key Findings
1. **KV cache growth** — Problem worsens with video length
2. **Distance-aware consolidation** — Temporal hierarchy for memory management
3. **Block merging** — Adjacent blocks merged based on temporal distance
4. **ByteDance research** — Practical video generation optimization

#### Actionable Next Steps
- [ ] Evaluate FadeMem for long video generation workloads
- [ ] Consider distance-aware KV management for your generative AI
- [ ] Apply temporal hierarchy to other autoregressive tasks

---

### 18. Express Language Modeling

**Source:** arXiv 2606.10944v1 (June 2026)  
**Authors:** Stanford  
**File:** `2606.10944v1`

#### Summary

This paper introduces Express, a tool for converting non-causal attention approximations into causal approximations with matching approximation guarantees. When combined with the state-of-the-art Thinformer approximation, Express improves upon the best known causal attention guarantees, delivering log^{3/2}(n)/s approximation error with only O(s) memory and O(s^2 log^2(n)) compression overhead.

#### Key Findings
1. **Attention approximation** — Convert between causal and non-causal
2. **Thinformer improvement** — Better than state-of-the-art
3. **Memory efficiency** — O(s) memory for sequence length n
4. **Triton implementation** — Efficient I/O-aware GPU kernel

#### Actionable Next Steps
- [ ] Consider Express for long-sequence workloads
- [ ] Evaluate attention approximations for your inference
- [ ] Review Thinformer + Express for memory-constrained scenarios

---

### 19. OpenPCC: Open and Confidential LLM Serving on Commodity TEEs

**Source:** arXiv 2606.11145v1 (June 2026)  
**Authors:** Various  
**File:** `2606.11145v1`

#### Summary

Generative AI applications like personal AI agents and chat assistants offer advanced capabilities, but LLMs require massive computation and are usually deployed in the cloud as APIs—meaning user requests are sent to a Cloud Inference Service. However, user requests now contain sensitive data that requires protection. OpenPCC enables open and confidential LLM serving on commodity Trusted Execution Environments (TEEs).

#### Key Findings
1. **Privacy concern** — User data sent to cloud inference services
2. **TEE-based serving** — Confidential computing with TEEs
3. **AMD SEV-SNP** — Hardware-backed security for inference
4. **Open implementation** — Open-source confidential LLM serving

#### Actionable Next Steps
- [ ] Evaluate TEE-based serving for sensitive inference workloads
- [ ] Consider OpenPCC for privacy-critical applications
- [ ] Review AMD SEV-SNP capabilities for your infrastructure

---

### 20. ReasonAlloc: Hierarchical Decoding-Time KV Cache Budget Allocation for Reasoning Models

**Source:** arXiv 2606.11164v1 (June 2026)  
**Authors:** Meta  
**File:** `2606.11164v1`

#### Summary

Long chain-of-thought (CoT) trajectories in large language model reasoning cause severe inference bottlenecks due to rapid key-value (KV) cache growth. Current decoding-time compression methods mitigate this via token eviction but typically apply uniform budgets across attention heads. ReasonAlloc introduces hierarchical decoding-time KV cache budget allocation that assigns budgets based on token utility scores per head, specifically designed for reasoning models with repetitive CoT trajectories.

#### Key Findings
1. **KV cache bottleneck** — Severe for reasoning models with long CoT
2. **Hierarchical allocation** — Per-head, per-token budget assignment
3. **Utility scores** — Based on attention head importance
4. **Meta research** — Directly applicable to o1/r1 style reasoning

#### Actionable Next Steps
- [ ] Critical for reasoning model inference — evaluate immediately
- [ ] Implement ReasonAlloc for your o1/r1 style deployments
- [ ] Profile KV cache growth in current reasoning workloads

---

## Paper Reviews (New — June 2026)

---

### 21. On the Limits of Performance Portability in Directive-Based GPU Programming

**Source:** arXiv 2606.12753v1 (June 2026)  
**Authors:** Alessandro Romeo, Nitin Shukla, Stefano Truzzi (CINECA, Politecnico di Milano)  
**File:** `2606.12753v1`

#### Summary

The transition of scientific applications to GPU-accelerated exascale systems is constrained by trade-offs between performance, portability, and productivity. This work evaluates the performance portability of directive-based GPU programming by porting gPLUTO, a production-grade magnetohydrodynamics code for astrophysical simulations, from OpenACC to OpenMP, and analyzing its performance on NVIDIA A100 (Leonardo Booster) and AMD MI250X (LUMI-G) devices.

#### Key Findings
1. **OpenACC vs OpenMP** — On NVIDIA, both achieve comparable performance due to shared compiler backend
2. **AMD MI250X challenges** — Performance portability gaps more significant on AMD GPUs
3. **Production-grade code** — Tests on real MHD simulation code, not synthetic benchmarks
4. **LUMI-G results** — Practical implications for AMD GPU clusters

#### Actionable Next Steps
- [ ] Review your directive-based GPU code for portability across NVIDIA/AMD
- [ ] Test OpenMP offloading vs OpenACC on your AMD MI300 infrastructure
- [ ] Consider target-agnostic directives for future code portability

---

### 22. WarpGuard: Protected-Site Control-Flow Integrity for CUDA SASS Binaries

**Source:** arXiv 2606.11871v1 (June 2026)  
**Authors:** Igor Santos-Grueiro  
**File:** `2606.11871v1`

#### Summary

Recent CUDA exploitation work shows that GPU memory bugs can escalate into device-side control-flow corruption, as kernels later consume corrupted return continuations, function pointers, dispatch-table entries, or branch targets. For deployed CUDA binaries, the relevant security boundary is executed NVIDIA SASS, after PTX lowering, inlining, and ABI decisions. WarpGuard is the first protected-site CFI system for CUDA device binaries operating on SASS level.

#### Key Findings
1. **SASS-level security** — CFI at the SASS level (post-PTX, post-inlining)
2. **Control-flow protection** — Protects against return continuation/function pointer corruption
3. **First of its kind** — No prior CFI work for CUDA device binaries
4. **Security boundary** — Addresses the gap between source/PTX and deployed SASS

#### Actionable Next Steps
- [ ] Evaluate WarpGuard for your CUDA deployment security
- [ ] Review GPU memory safety in your CUDA kernels
- [ ] Consider CFI for production CUDA workloads

---

### 23. Making Locality-aware GEMM Compatible with Page-Granularity Placement on Chiplet GPUs

**Source:** arXiv 2606.11718v2 (June 2026)  
**Authors:** Euijun Chung, Jae Hyung Ju, Hyesoon Kim (Georgia Tech)  
**File:** `2606.11718v2`

#### Summary

Multi-chiplet GPUs scale compute throughput and high-bandwidth memory (HBM) capacity, but their non-uniform memory system makes locality between chiplets and their data critical to performance and energy efficiency. Locality-aware scheduling and data placement identify which data should reside near each chiplet. However, in GEMM, locality-aware data placement often becomes incompatible with fixed page-granularity data interleaving. This paper proposes Chiplet-Cooperative GEMM to resolve the incompatibility.

#### Key Findings
1. **Chiplet GPU locality** — Critical for MI300X and similar multi-chiplet architectures
2. **GEMM page-granularity** — Optimal granularity varies across workloads
3. **Chiplet-Cooperative approach** — Resolves placement incompatibility
4. **Directly relevant** — Very relevant to your MI300X workloads on asrock

#### Actionable Next Steps
- [ ] Apply chiplet-aware GEMM optimization to your MI300X workloads
- [ ] Profile locality-aware data placement on your multi-GPU setup
- [ ] Consider page-granularity tuning for your matrix workloads

---

### 24. Gefen: Optimized Stochastic Optimizer

**Source:** arXiv 2606.13894v1 (June 2026)  
**Authors:** Nadav Benedek, Tomer Koren, Ohad Fried (Google Research)  
**File:** `2606.13894v1`

#### Summary

AdamW is a default optimizer for modern deep learning, but its first and second moment states add roughly two parameter-sized buffers to training memory. Gefen is a memory-efficient optimizer that automatically shares second-moment estimates across parameter blocks and quantizes the first moment using a learned codebook, reducing AdamW's memory footprint by ~8× while maintaining the same performance—a reduction of 6.5 GiB per billion parameters.

#### Key Findings
1. **8× memory reduction** — Significant savings vs AdamW
2. **Second-moment sharing** — Shares estimates across parameter blocks
3. **First-moment quantization** — Uses learned codebook for quantization
4. **6.5 GiB/billion params** — Concrete savings for large models

#### Actionable Next Steps
- [ ] Evaluate Gefen for memory-constrained training workloads
- [ ] Consider for large model training on limited GPU memory
- [ ] Test against other memory-efficient optimizers (Adam8bit, Sophia)

---

### 25. Multi-Bitwidth Quantization for LLMs Using Additive Codebooks

**Source:** arXiv 2606.12876v1 (June 2026)  
**Authors:** Liza Babaoglu, Shuangyi Chen, Ashish Khisti (MIT, NVIDIA)  
**File:** `2606.12876v1`

#### Summary

As LLMs are increasingly deployed across heterogeneous hardware with varying resource constraints, the ability to adaptively manage the trade-off between performance and efficiency without retraining is critical. Drop-by-Drop is a novel multi-bitwidth post-training quantization framework that enables inference-time precision control over LLM weights from a single trained model, theoretically grounded in information theory and successive refinement.

#### Key Findings
1. **Multi-bitwidth inference** — Single model, adjustable precision at runtime
2. **No retraining needed** — Post-training quantization approach
3. **Heterogeneous deployment** — Targets varying hardware constraints
4. **Information theory basis** — Based on successive refinement

#### Actionable Next Steps
- [ ] Evaluate Drop-by-Drop for multi-tenant inference serving
- [ ] Consider adaptive precision for varying workload demands
- [ ] Test on your inference infrastructure

---

### 26. RATS! Patches Talk Through Registers: Emergent Parts in Register Attention Transformers

**Source:** arXiv 2606.14701v1 (June 2026)  
**Authors:** Timing Yang, Predrag Neskovic, Jansen Seheult  
**File:** `2606.14701v1`

#### Summary

When humans see a bird, they recognize far more than just "bird"—they see a head, wings, and talons, a structured assembly of reusable parts identified across every bird. This paper asks whether a self-supervised visual model can discover the same compositional structure. RATS (Register Attention Transformers) decomposes the classification token into N learnable register tokens that route patch information through an L→N→N→L bottleneck via compress-communicate-broadcast attention.

#### Key Findings
1. **Compositional structure** — Models learn parts like humans do
2. **Register tokens** — New approach to token-based vision models
3. **Compress-communicate-broadcast** — Three-step attention mechanism
4. **Self-supervised learning** — Discovers structure without labels

#### Actionable Next Steps
- [ ] Track RATS for computer vision workloads
- [ ] Consider register-based attention for your vision models
- [ ] Evaluate for multimodal AI applications

---

## Paper Reviews (July 2026) — Today's Kernel Digest

---

### 57. CloakLM: Obfuscating GPU Memory Layout to Mitigate Model Ex-filtration for Serving

**Source:** arXiv 2606.18400v1 (June 2026)  
**Authors:** Various  
**File:** `2606.18400v1.pdf`

#### Summary

CloakLM proposes obfuscating GPU memory layout to prevent model exfiltration attacks in LLM serving. By randomizing memory mapping, it becomes significantly harder for attackers to extract model weights from GPU memory during serving.

#### Key Findings
1. **Memory layout obfuscation** — Randomization prevents model extraction
2. **Model exfiltration mitigation** — Protects against GPU memory reading attacks
3. **Serving integration** — Works with vLLM/SGLang serving stacks

#### Actionable Next Steps
- [ ] Evaluate for multi-tenant inference serving security
- [ ] Consider for protecting proprietary model weights

---

### 58. SwiftCache: Efficient LLM Serving for Multi-turn Conversations with Heterogeneous KV Cache Sharing

**Source:** arXiv 2606.16135v1 (June 2026)  
**Authors:** Various  
**File:** `2606.16135v1.pdf`

#### Summary

SwiftCache introduces heterogeneous KV cache sharing for multi-turn conversations, optimizing cache utilization across different conversation contexts and significantly improving throughput for chat-based LLM serving.

#### Key Findings
1. **Heterogeneous KV cache sharing** — Different sharing strategies per context type
2. **Multi-turn optimization** — Specifically targets conversational AI
3. **Cache efficiency** — Reduces memory pressure in long conversations

#### Actionable Next Steps
- [ ] Implement for vLLM/SGLang inference optimization
- [ ] Profile KV cache usage improvements

---

### 59. JetFlow: Breaking the Scaling Ceiling of Speculative Decoding with Parallel Tree Drafting

**Source:** arXiv 2606.18394v1 (June 2026)  
**Authors:** Various  
**File:** `2606.18394v1.pdf`

#### Summary

JetFlow addresses the scaling limitations of speculative decoding by introducing parallel tree drafting, allowing multiple draft branches to be verified simultaneously and significantly improving inference throughput.

#### Key Findings
1. **Parallel tree drafting** — Multiple speculative paths in parallel
2. **Scaling ceiling breakthrough** — Overcomes traditional spec-decoding limits
3. **Draft verification** — Efficient verification of multiple branches

#### Actionable Next Steps
- [ ] Evaluate for high-throughput inference workloads
- [ ] Consider integration with vLLM speculative decoding

---

### 60. SMEPilot: Characterizing and Optimizing LLM Inference with Scalable Matrix Extensions

**Source:** arXiv 2606.16332v1 (June 2026)  
**Authors:** Various  
**File:** `2606.16332v1.pdf`

#### Summary

SMEPilot characterizes CPU Scalable Matrix Extensions (SMEx) for LLM inference optimization, demonstrating significant speedups by leveraging these new CPU instructions for matrix operations critical to transformer inference.

#### Key Findings
1. **Scalable Matrix Extensions** — New CPU instructions for AI
2. **CPU-LLM optimization** — Focuses on CPU-based inference
3. **SMEx benchmarks** — Comprehensive performance analysis

#### Actionable Next Steps
- [ ] Review for CPU inference optimization opportunities
- [ ] Consider for edge CPU-based LLM serving

---

### 61. daVinci-kernel: Co-Evolving Skill Selection, Summarization, and Utilization via RL for GPU Kernel Optimization

**Source:** arXiv 2606.16497v1 (June 2026)  
**Authors:** Various  
**File:** `2606.16497v1.pdf`

#### Summary

daVinci-kernel uses reinforcement learning to co-evolve skill selection, summarization, and utilization for GPU kernel optimization, automatically discovering effective kernel patterns without manual programming.

#### Key Findings
1. **RL-based kernel selection** — AI-driven kernel optimization
2. **Skill summarization** — Learns to compress kernel strategies
3. **GPU kernel generation** — Automated kernel creation

#### Actionable Next Steps
- [ ] Explore for automated kernel tuning on MI300X
- [ ] Consider for HIP kernel optimization workflows

---

### 62. Diagonal-Budgeted Trotterization for Efficient Quantum Hamiltonian Simulation

**Source:** arXiv 2606.16959v1 (June 2026)  
**Authors:** Various  
**File:** `2606.16959v1.pdf`

#### Summary

This paper presents diagonal-budgeted Trotterization for quantum Hamiltonian simulation, optimizing the decomposition of quantum operations for more efficient simulation on GPU-based quantum simulators.

#### Key Findings
1. **Trotterization optimization** — Improved quantum simulation algorithm
2. **Quantum Hamiltonian simulation** — Applications in quantum computing
3. **GPU acceleration** — Leverages GPUs for quantum simulation

#### Actionable Next Steps
- [ ] Track for quantum computing workflows on GPUs

---

### 63. From Tokens to Regions: CUDA-Sensitive Instruction Tuning for GPU Kernel Generation

**Source:** arXiv 2606.16231v1 (June 2026)  
**Authors:** Various  
**File:** `2606.16231v1.pdf`

#### Summary

This work introduces CUDA-sensitive instruction tuning for GPU kernel generation, using LLM fine-tuning to produce optimized CUDA kernels specifically tailored to hardware characteristics.

#### Key Findings
1. **Instruction tuning for CUDA** — LLM-based kernel generation
2. **Token-to-region mapping** — Understanding CUDA code structure
3. **Hardware-aware generation** — Architecture-specific optimization

#### Actionable Next Steps
- [ ] Evaluate for automated CUDA kernel generation

---

### 64. AoiZora: Topology-Aware Auto-Parallel Optimization for Inference of Diffusion Transformers

**Source:** arXiv 2606.17566v1 (June 2026)  
**Authors:** Various  
**File:** `2606.17566v1.pdf`

#### Summary

AoiZora provides topology-aware auto-parallel optimization specifically for diffusion transformer inference, optimizing computation distribution across accelerator topologies for maximum efficiency.

#### Key Findings
1. **Topology-aware optimization** — Network topology considerations
2. **Diffusion transformer inference** — Specialized for image generation
3. **Auto-parallel** — Automated distribution strategies

#### Actionable Next Steps
- [ ] Consider for diffusion model serving on multi-GPU systems

---

### 65. A performance portable fast Ewald summation for Stokes flow

**Source:** arXiv 2606.19059v1 (June 2026)  
**Authors:** Various  
**File:** `2606.19059v1.pdf`

#### Summary

This paper presents a performance-portable fast Ewald summation method for Stokes flow computations, achieving efficient execution across different GPU architectures including AMD GPUs.

#### Key Findings
1. **Performance portability** — Works across NVIDIA and AMD
2. **Ewald summation** — Efficient particle interaction计算
3. **AMD GPU support** — Specifically validates on AMD hardware

#### Actionable Next Steps
- [ ] Validate on AMD MI300X for HPC workloads

---

### 66. Pulse: Training Acceleration for Large Diffusion Models with Automatic Pipeline Parallelism

**Source:** arXiv 2606.19163v1 (June 2026)  
**Authors:** Various  
**File:** `2606.19163v1.pdf`

#### Summary

Pulse introduces automatic pipeline parallelism for large diffusion model training, dynamically partitioning computation to maximize GPU utilization and reduce training time.

#### Key Findings
1. **Pipeline parallelism** — Automatic stage partitioning
2. **Diffusion model training** — Specialized for image generation models
3. **Automatic scheduling** — No manual partitioning required

#### Actionable Next Steps
- [ ] Evaluate for large-scale diffusion model training

---

### 67. Beyond Prediction: Tail-Aware Scheduling for LLM Inference

**Source:** arXiv 2606.18431v1 (June 2026)  
**Authors:** Various  
**File:** `2606.18431v1.pdf`

#### Summary

Beyond Prediction introduces tail-aware scheduling for LLM inference that specifically targets P99 latency reduction through intelligent request ordering and resource allocation.

#### Key Findings
1. **Tail-aware scheduling** — Optimizes for worst-case latency
2. **P99 reduction** — Addresses long-tail latency
3. **Request ordering** — Intelligent queue management

#### Actionable Next Steps
- [ ] Implement for latency-sensitive inference serving

---

### 68. TurboServe: Serving Streaming Video Generation Efficiently and Economically

**Source:** arXiv 2606.19271v1 (June 2026)  
**Authors:** Various  
**File:** `2606.19271v1.pdf`

#### Summary

TurboServe addresses the challenges of serving streaming video generation models, providing efficient and economical deployment strategies for real-time video synthesis workloads.

#### Key Findings
1. **Streaming video serving** — Real-time video generation
2. **Efficient deployment** — Resource optimization
3. **Economic serving** — Cost reduction strategies

#### Actionable Next Steps
- [ ] Consider for video generation inference serving

---

### 69. Unified KV Pooling to Accelerate Long-Context LLM Serving

**Source:** arXiv 2606.14779v1 (June 2026)  
**Authors:** Various  
**File:** `2606.14779v1.pdf`

#### Summary

Unified KV Pooling proposes a novel approach to managing KV cache memory for long-context LLM serving, pooling and sharing cache across requests to maximize memory efficiency.

#### Key Findings
1. **Long-context optimization** — Handles very long sequences
2. **Unified KV pooling** — Shared cache management
3. **Memory efficiency** — Reduces KV cache memory footprint

#### Actionable Next Steps
- [ ] Profile for long-context inference workloads

---

### 70. Bifrost: Hybrid TEE-FHE Inference for Privacy-Preserving Transformer and LLM Serving

**Source:** arXiv 2606.17421v1 (June 2026)  
**Authors:** Various  
**File:** `2606.17421v1.pdf`

#### Summary

Bifrost combines Trusted Execution Environments (TEE) with Fully Homomorphic Encryption (FHE) for privacy-preserving LLM inference, enabling secure computation on sensitive data.

#### Key Findings
1. **Hybrid TEE-FHE** — Combined security approaches
2. **Privacy-preserving inference** — Protects user data
3. **Confidential computing** — Hardware-backed security

#### Actionable Next Steps
- [ ] Evaluate for sensitive inference workloads

---

### 71. CUTh-Solver: GPU-Accelerated Sparse Matrix Solver for High-Resolution Thermal Simulation of 3D ICs

**Source:** arXiv 2606.17850v1 (June 2026)  
**Authors:** Various  
**File:** `2606.17850v1.pdf`

#### Summary

CUTh-Solver presents a GPU-accelerated sparse matrix solver optimized for 3D integrated circuit thermal simulation, enabling high-resolution thermal analysis at unprecedented speeds.

#### Key Findings
1. **3D thermal simulation** — IC design optimization
2. **Sparse matrix solver** — GPU-accelerated computation
3. **High resolution** - Enables finer thermal analysis

#### Actionable Next Steps
- [ ] Consider for EDA/thermal workloads

---

### 72. Inference Optimal Long Run Variance Estimation with Lugsail Kernels

**Source:** arXiv 2606.17369v1 (June 2026)  
**Authors:** Various  
**File:** `2606.17369v1.pdf`

#### Summary

This paper presents inference-optimal long run variance estimation using Lugsail kernels, providing statistically rigorous methods for analyzing time-series inference results.

#### Key Findings
1. **Lugsail kernels** — Novel statistical methodology
2. **Variance estimation** — Long-run variance analysis
3. **Statistical rigor** — Improved confidence intervals

#### Actionable Next Steps
- [ ] Track for inference benchmarking methodology

---

### 73. Kernel-Based Functional Balancing for Causal Inference with Compositional Treatments

**Source:** arXiv 2606.17308v1 (June 2026)  
**Authors:** Various  
**File:** `2606.17308v1.pdf`

#### Summary

Kernel-based functional balancing provides new methods for causal inference with compositional treatments, using kernel learning to estimate treatment effects more accurately.

#### Key Findings
1. **Functional balancing** — Novel causal inference approach
2. **Kernel methods** — Statistical learning techniques
3. **Compositional treatments** — Complex treatment analysis

#### Actionable Next Steps
- [ ] Review for ML system optimization research

---

### 74. Plug-and-Adapt: Multimodal Coreference Resolution at First Sight with a Pretrained Alignment Model

**Source:** arXiv 2606.17950v1 (June 2026)  
**Authors:** Various  
**File:** `2606.17950v1.pdf`

#### Summary

Plug-and-Adapt addresses multimodal coreference resolution by using pretrained alignment models, enabling zero-shot transfer to new domains without fine-tuning.

#### Key Findings
1. **Multimodal coreference** — Text-image linking
2. **Pretrained alignment** — Cross-modal representations
3. **First-sight adaptation** — Zero-shot capabilities

#### Actionable Next Steps
- [ ] Evaluate for multimodal AI applications

---

### 75. AIA: A 16nm Multicore SoC for Approximate Inference Acceleration Exploiting Non-normalized Knuth-Yao Sampling

**Source:** arXiv 2606.16148v1 (June 2026)  
**Authors:** Various  
**File:** `2606.16148v1.pdf`

#### Summary

This paper presents a 16nm multicore SoC optimized for approximate inference using non-normalized Knuth-Yao sampling, achieving significant energy efficiency improvements.

#### Key Findings
1. **Approximate inference** — Accuracy-efficiency trade-offs
2. **Knuth-Yao sampling** — Efficient random sampling
3. **16nm SoC** — Custom hardware implementation

#### Actionable Next Steps
- [ ] Track for edge AI hardware developments

---

### 76. AIA: A Customized Multi-core RISC-V SoC for Discrete Sampling Workloads in 16 nm

**Source:** arXiv 2606.16143v1 (June 2026)  
**Authors:** Various  
**File:** `2606.16143v1.pdf`

#### Summary

A customized RISC-V SoC for discrete sampling workloads, demonstrating how custom ISA extensions can accelerate probabilistic computing tasks.

#### Key Findings
1. **RISC-V extensions** — Custom instructions for sampling
2. **Discrete sampling** — Probabilistic computation
3. **16nm implementation** — Practical chip design

#### Actionable Next Steps
- [ ] Monitor for RISC-V AI accelerator developments

---

### 77. From the NYU Ultracomputer to Modern Exascale: A Historical and Architectural Survey of In-Network Computing

**Source:** arXiv 2606.16819v1 (June 2026)  
**Authors:** Various  
**File:** `2606.16819v1.pdf`

#### Summary

This paper provides a comprehensive historical survey of in-network computing from the NYU Ultracomputer to modern exascale systems, highlighting the evolution of compute-intensive networking.

#### Key Findings
1. **Historical survey** — From Ultracomputer to exascale
2. **In-network computing** — RDMA and smart NICs
3. **Architecture evolution** — 40+ years of progress

#### Actionable Next Steps
- [ ] Review for infrastructure planning context

---

### 78. Mixed-Precision Communication-Avoiding SGD for Generalized Linear Models on GPUs

**Source:** arXiv 2606.18463v1 (June 2026)  
**Authors:** Various  
**File:** `2606.18463v1.pdf`

#### Summary

This work presents mixed-precision communication-avoiding SGD for training generalized linear models on GPUs, reducing communication overhead while maintaining accuracy.

#### Key Findings
1. **Mixed-precision training** — Reduced memory and communication
2. **Communication avoiding** — Minimize data transfer
3. **GLM optimization** — Linear models, logistic regression

#### Actionable Next Steps
- [ ] Evaluate for large-scale GLM training

---

### 79. KATANA: A Fast, Low-Power Mapping of Kalman Filters onto Edge NPUs for Real-Time Tracking

**Source:** arXiv 2606.14992v1 (June 2026)  
**Authors:** Various  
**File:** `2606.14992v1.pdf`

#### Summary

KATANA maps Kalman filters onto edge NPUs for real-time tracking applications, achieving low-power operation suitable for battery-powered edge devices.

#### Key Findings
1. **Kalman filter optimization** — State estimation
2. **Edge NPU mapping** — Specialized hardware mapping
3. **Real-time tracking** — Low-latency requirements

#### Actionable Next Steps
- [ ] Consider for edge AI deployment

---

### 80. BIDENT: Heterogeneous Operator-level Mapping for Efficient Edge Inference

**Source:** arXiv 2606.05271v1 (June 2026)  
**Authors:** Various  
**File:** `2606.05271v1.pdf`

#### Summary

BIDENT provides heterogeneous operator-level mapping for efficient edge inference, optimizing how different neural network operators map to heterogeneous edge hardware.

#### Key Findings
1. **Heterogeneous mapping** — Cross-device optimization
2. **Operator-level** — Fine-grained scheduling
3. **Edge inference** — Efficient deployment

#### Actionable Next Steps
- [ ] Review for edge deployment optimization

---

### 81. Maestro: Workload-Aware Cross-Cluster Scheduling for LLM-Based Multi-Agent Systems

**Source:** arXiv 2606.12950v1 (June 2026)  
**Authors:** Various  
**File:** `2606.12950v1.pdf`

#### Summary

Maestro introduces workload-aware cross-cluster scheduling for multi-agent LLM systems, intelligently distributing agent tasks across clusters based on workload characteristics.

#### Key Findings
1. **Multi-agent scheduling** — Orchestrating multiple agents
2. **Cross-cluster** — Distributed system optimization
3. **Workload-aware** - Dynamic resource allocation

#### Actionable Next Steps
- [ ] Evaluate for multi-agent inference systems

---

### 82. Litespark Inference For CPUs: Ultra-Fast SIMD Framework for Ternary (1.58-bit) Language Models

**Source:** arXiv 2605.06485v2 (May 2026)  
**Authors:** Various  
**File:** `2605.06485v1.pdf`

#### Summary

Litespark provides an ultra-fast SIMD framework for running ternary (1.58-bit) language models on CPU, achieving remarkable inference speeds with minimal accuracy loss.

#### Key Findings
1. **Ternary quantization** — 1.58-bit models
2. **SIMD optimization** — CPU vector instructions
3. **Fast CPU inference** — Near-real-time performance

#### Actionable Next Steps
- [ ] Evaluate for CPU-only inference scenarios

---

### 83. VaultxGPU: GPU-Accelerated Blockchain Consensus

**Source:** arXiv 2606.14007v1 (June 2026)  
**Authors:** Various  
**File:** `2606.14007v1.pdf`

#### Summary

VaultxGPU accelerates blockchain consensus mechanisms using GPUs, demonstrating significant throughput improvements for proof-of-stake and other consensus protocols.

#### Key Findings
1. **GPU blockchain** — Consensus acceleration
2. **Proof-of-stake** — Modern blockchain protocols
3. **Throughput** — Transaction processing speed

#### Actionable Next Steps
- [ ] Monitor for blockchain infrastructure

---

### 84. PortBERT: Navigating the Depths of Portuguese Language Models

**Source:** arXiv 2606.02100v1 (June 2026)  
**Authors:** Various  
**File:** `2606.02100v1.pdf`

#### Summary

PortBERT explores Portuguese language model development, providing insights into multilingual LLM training and evaluation for non-English languages.

#### Key Findings
1. **Portuguese NLP** — Multilingual model development
2. **Language-specific tuning** — Specialized training
3. **Evaluation** — Multilingual benchmarks

#### Actionable Next Steps
- [ ] Review for multilingual deployment

---

### 85. i1: A Simple and Fully Open Recipe for Strong Text-to-Image Models

**Source:** arXiv 2606.11289v1 (June 2026)  
**Authors:** Various  
**File:** `2606.11289v1.pdf`

#### Summary

i1 presents a fully open recipe for training strong text-to-image models on TPU infrastructure, providing reproducible training procedures for image generation.

#### Key Findings
1. **Open recipe** — Reproducible training
2. **TPU training** — Google infrastructure
3. **Text-to-image** — Image generation models

#### Actionable Next Steps
- [ ] Consider for image generation training

---

### 86. Monte Cimone v3: Where RISC-V Stands in High-Performance Computing

**Source:** arXiv 2605.22831v2 (May 2026)  
**Authors:** Various  
**File:** `2605.22831v1.pdf`

#### Summary

Monte Cimone v3 benchmarks RISC-V processors for HPC workloads, providing the first comprehensive analysis of RISC-V performance in high-performance computing contexts.

#### Key Findings
1. **RISC-V benchmarking** — Architecture evaluation
2. **HPC performance** — Supercomputer workloads
3. **Architecture comparison** — vs x86 and ARM

#### Actionable Next Steps
- [ ] Track RISC-V for future infrastructure

---

### 87. Quantum Encryption Resilience Score (QERS) for MQTT, HTTP, and HTTPS under Post-Quantum Cryptography

**Source:** arXiv 2601.13423v1 (Jan 2026)  
**Authors:** Jonatan Rassekhnia  
**File:** `2601.13423v1.pdf`

#### Summary

QERS provides a scoring system for evaluating post-quantum cryptography resilience in IoT communication protocols, addressing the upcoming quantum threat to encryption.

#### Key Findings
1. **Post-quantum cryptography** — Quantum-resistant encryption
2. **Protocol analysis** — MQTT, HTTP, HTTPS
3. **Resilience scoring** — Security evaluation framework

#### Actionable Next Steps
- [ ] Plan for PQC migration in infrastructure

---

### 88. ABI: A tightly integrated, unified, sparsity-aware, reconfigurable, compute near-register file/cache

**Source:** arXiv 2602.14262v3 (Feb 2026)  
**Authors:** Various  
**File:** `2602.14262v1.pdf`

#### Summary

ABI presents a novel compute-near-storage architecture with reconfigurable sparsity-aware processing, placing computation close to memory for maximum efficiency.

#### Key Findings
1. **Near-memory computing** — Computation in memory hierarchy
2. **Sparsity-aware** — Optimized for sparse workloads
3. **Reconfigurable** — Flexible architecture

#### Actionable Next Steps
- [ ] Monitor for near-memory computing trends

---

### 89. The Role of High-Performance GPU Resources in Large Language Model Based Radiology Imaging Diagnosis

**Source:** arXiv 2509.16328v2 (Sep 2025)  
**Authors:** Jyun-Ping Kao  
**File:** `2509.16328v1.pdf`

#### Summary

This paper reviews the role of high-performance GPUs in LLM-based radiology imaging diagnosis, analyzing the hardware requirements for clinical AI deployment.

#### Key Findings
1. **Clinical AI** — Medical imaging with LLMs
2. **GPU requirements** — Hardware specifications
3. **Deployment** — Production considerations

#### Actionable Next Steps
- [ ] Review for medical AI infrastructure planning

---

### 90. FPGA-Accelerated RISC-V ISA Extensions for Efficient Neural Network Inference on Edge Devices

**Source:** arXiv 2511.06955v1 (Nov 2025)  
**Authors:** Arya Parameshwara, Santosh Hanamappa Mokashi  
**File:** `2511.06955v1.pdf`

#### Summary

This paper presents FPGA-accelerated RISC-V ISA extensions for efficient edge neural network inference, demonstrating custom instructions that significantly improve efficiency.

#### Key Findings
1. **RISC-V ISA extensions** — Custom instructions
2. **FPGA acceleration** — Hardware implementation
3. **Edge inference** — Low-power AI

#### Actionable Next Steps
- [ ] Evaluate for edge AI deployments

---

### 91. APU-Accelerated Large Eddy Simulation with the Discontinuous Galerkin Solver GALÆXI

**Source:** arXiv 2606.18927v1 (June 2026)  
**Authors:** Various  
**File:** `2606.18927v1.pdf`

#### Summary

This paper demonstrates APU-accelerated large eddy simulation using the GALÆXI discontinuous Galerkin solver, achieving high performance on AMD integrated GPUs.

#### Key Findings
1. **APU utilization** — Integrated GPU performance
2. **Discontinuous Galerkin** — High-order CFD method
3. **AMD support** — Validates on AMD APUs

#### Actionable Next Steps
- [ ] Consider for CFD workloads on AMD hardware

---

## Adding New Papers

When adding new papers to this directory, follow this template:

```markdown
### N. [Paper Title]

**Source:** [arXiv ID / Conference] ([Month Year])  
**Authors:** [Author List]  
**File:** [filename]

#### Summary
[2-3 sentence summary of the paper's focus and context]

#### Key Findings
1. [Finding 1]
2. [Finding 2]
3. [Finding 3]

#### Actionable Next Steps
- [ ] [Action item 1]
- [ ] [Action item 2]
```

## Related Research

- See also: `fio-benchmark-analysis` skill for storage benchmarking
- See also: `amd-gpu-memory-benchmarking` for GPU memory analysis
- See also: `amd-smi` skill for AMD GPU health monitoring