# Storage Directory

This directory contains papers related to distributed file systems, parallel file systems, HPC storage, and storage performance optimization.

## Paper Reviews

---

### 1. Icicle: Scalable Metadata Indexing and Real-Time Monitoring for HPC File Systems

**Source:** arXiv 2604.10295 (April 2026)  
**Authors:** Haochen Pan, Ryan Chard, Song Young Oh, Maxime Gonthier, Valérie Hayot-Sasson, Geoffrey Lentner, Joe Bottigliero, Rachana Ananthakrishnan, Kyle Chard, Ian Foster (U Chicago, Argonne, Purdue, École de technologie supérieure)  
**File:** `Icicle_Scalable_Metadata_Indexing_and_Real_Time_Monitoring_for_HPC_File_Systems.pdf`

#### Summary
Modern HPC file systems can contain billions of files and hundreds of petabytes of data, making even simple queries intractable. Traditional utilities like `find` and `du` fail to scale. Icicle is a scalable framework for continuous file system metadata indexing and monitoring that maintains a unified, up-to-date, queryable view of file system state with both periodic snapshot ingestion and event-based real-time synchronization.

#### Key Findings
1. **Metadata at scale is a fundamental problem** — Billions of files make traditional file system queries impossible
2. **Dual ingestion pipeline** — Supports both bulk metadata snapshots (batch) and event-based real-time sync
3. **Multi-granular queries** — Enables analysis at individual file, aggregate, and summary levels
4. **Precomputed distributional statistics** — Stores min, p25, p50, p75, max, mean for size, atime, ctime, mtime
5. **Horizontal scaling** — Monitor instances scale by aligning with storage server domains
6. **Query examples supported** — "Which large files have low access frequency?", "Total storage per project", "Which users have most small files?"

#### Actionable Next Steps
- [ ] Evaluate Icicle for your HPC cluster's metadata management needs
- [ ] Consider implementing continuous metadata indexing for large-scale file systems
- [ ] Review what queries your operations team struggles with — map to Icicle capabilities
- [ ] Assess whether event-based ingestion is feasible with your storage backend (Lustre, GPFS, etc.)

---

### 2. STELLAR: Storage Tuning Engine Leveraging LLM Autonomous Reasoning for High Performance Parallel File Systems

**Source:** arXiv 2602.23220 (February 2026)  
**Authors:** Chris Egersdoerfer, Philip Carns, Shane Snyder, Robert Ross, Dong Dai (University of Delaware, Argonne National Laboratory)  
**File:** `STELLAR_Storage_Tuning_Engine_Leveraging_LLM_Autonomous_Reasoning_for_High_Performance_Parallel_File_Systems.pdf`

#### Summary
I/O performance is crucial for data-intensive scientific computing, but tuning large-scale storage systems is complex and manpower-intensive. STELLAR is an autonomous tuner for parallel file systems that uses LLM-based reasoning to select near-optimal configurations within 5 attempts—fundamentally different from existing autotuning methods that require hundreds of thousands of iterations.

#### Key Findings
1. **LLMs can tune storage like humans** — STELLAR mimics human expert reasoning, achieving near-optimal configs in ~5 attempts vs hundreds for traditional autotuning
2. **RAG mechanism for parameter extraction** — Uses retrieval-augmented generation to identify high-impact tunable parameters (e.g., stripe_size, stripe_count, max_rpc_in_flight)
3. **Per-application tuning required** — Different applications have distinct I/O patterns and respond differently to the same parameter values
4. **Key Lustre parameters** — stripe_size, stripe_count, max_rpc_in_flight, max_pages_per_rpc have significant I/O impact
5. **Knowledge distillation** — Accumulated tuning knowledge becomes valuable for reducing future tuning trials

#### Actionable Next Steps
- [ ] Review current Lustre/stripe configuration defaults vs application needs
- [ ] Consider implementing LLM-based autotuning for your storage infrastructure
- [ ] Document tuning knowledge for your specific HPC platform to accelerate future tuning
- [ ] Focus on high-impact tunable parameters rather than brute-force tuning all parameters

---

### 3. CARAT: Client-Side Adaptive RPC and Cache Co-Tuning for Parallel File Systems

**Source:** arXiv 2602.22423 (February 2026)  
**Authors:** Md Hasanur Rashid, Nathan R. Tallent, Forrest Sheng Bao, Dong Dai (University of Delaware, PNNL, Iowa State)  
**File:** `CARAT_Client_Side_Adaptive_RPC_and_Cache_Co_Tuning_for_Parallel_File_Systems.pdf`

#### Summary
Tuning parallel file systems remains challenging due to complex I/O paths, diverse patterns, and dynamic conditions. CARAT is an ML-guided framework that co-tunes client-side RPC and caching parameters using only locally observable metrics—enabling each client to make independent, intelligent tuning decisions online without requiring global coordination.

#### Key Findings
1. **Decentralized, local-only metrics** — Each client tunes independently using only locally observable metrics, no global coordination needed
2. **Co-tuning RPC and cache** — Jointly optimizes RPC parameters (concurrency, transfer size) and cache settings
3. **Up to 3× performance improvement** — Achieved over default or static configurations in evaluations
4. **Online and adaptive** — Responds to real-time changes in application I/O behaviors and system states
5. **Scalable** — No single point of coordination bottleneck; each client operates independently

#### Actionable Next Steps
- [ ] Evaluate CARAT for Lustre deployments with diverse I/O patterns
- [ ] Consider implementing client-side RPC tuning for your workloads
- [ ] Assess the value of moving from static to dynamic, adaptive configuration
- [ ] Test with multi-client deployments to validate decentralized approach

---

### 4. DIAL: Decentralized I/O AutoTuning via Learned Client-side Local Metrics for Parallel File System

**Source:** arXiv 2602.22392 (February 2026)  
**Authors:** Md Hasanur Rashid, Xinyi Li, Youbiao He, Forrest Sheng Bao, Dong Dai (University of Delaware, Iowa State)  
**File:** `DIAL_Decentralized_I_O_AutoTuning_via_Learned_Client_side_Local_Metrics_for_Parallel_File_System.pdf`

#### Summary
Enabling efficient, high-performance data access in parallel file systems is critical, but existing autotuning approaches rely heavily on extensive global runtime metrics and accurate I/O pattern modeling—creating overhead that limits fine-grained, dynamic tuning. DIAL takes a decentralized approach, treating each I/O client as independent and tuning using only locally observable metrics with ML models.

#### Key Findings
1. **Decentralized approach** — Each client operates independently without global coordination
2. **Local metrics only** — Uses locally observable metrics, avoiding overhead of global monitoring
3. **ML-driven** — Leverages machine learning models to map local metrics to optimal configurations
4. **Reduces overhead** — Eliminates the heavy overhead of global pattern extraction and modeling

#### Actionable Next Steps
- [ ] Compare DIAL's approach to CARAT for your specific use case
- [ ] Consider local-metric-based tuning for reducing monitoring infrastructure overhead
- [ ] Evaluate whether decentralized tuning fits your cluster's architecture

---

### 5. AdapTBF: Decentralized Bandwidth Control via Adaptive Token Borrowing for HPC Storage

**Source:** arXiv 2602.22409 (February 2026)  
**Authors:** Md Hasanur Rashid, Dong Dai (University of Delaware)  
**File:** `AdapTBF_Decentralized_Bandwidth_Control_via_Adaptive_Token_Borrowing_for_HPC_Storage.pdf`

#### Summary
HPC applications share global storage systems but can consume disproportional I/O bandwidth—hindering larger jobs. Existing Token Bucket Filter (TBF) mechanisms strictly limit bandwidth proportionally, leading to wasted bandwidth when applications aren't performing I/O. AdapTBF introduces adaptive token borrowing, allowing applications to temporarily utilize unused bandwidth while preventing interference with larger jobs.

#### Key Findings
1. **Problem: bandwidth hogging** — Small jobs can consume excessive I/O bandwidth, hindering larger jobs
2. **Existing TBF limitations** — Strict proportional limits waste storage server bandwidth during idle periods
3. **Adaptive token borrowing** — Applications can temporarily borrow unused bandwidth from others
4. **Prevents interference** — Maintains fairness while maximizing overall I/O efficiency
5. **Bursty I/O patterns** — Specifically addresses HPC applications' characteristic short, bursty requests

#### Actionable Next Steps
- [ ] Audit current I/O bandwidth allocation fairness in your HPC cluster
- [ ] Consider implementing adaptive bandwidth control for multi-tenant storage
- [ ] Evaluate token bucket configurations for your storage servers
- [ ] Test AdapTBF approach with representative bursty I/O workloads

---

## Adding New Papers

When adding new papers to this directory, follow this template:

```markdown
### N. [Paper Title]

**Source:** [arXiv ID / Conference]  
**Authors:** [Author List]  
**File:** [filename.pdf]

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

- See also: `large-scale-nfs-research` skill for arXiv search methodology on NFS and distributed file systems
- See also: `fio-benchmark-analysis` skill for running your own storage benchmarks