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