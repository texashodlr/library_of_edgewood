# References

This file contains the reference lists from papers in this directory.

---

## 1. Icicle: Scalable Metadata Indexing and Real-Time Monitoring for HPC File Systems

**arXiv:** 2604.10295

[6] GUFI. https://github.com/melmothx/gufi

[7] Brindexer. https://github.com/melmothx/amusewiki/blob/main/lib/AMuseWiki/Export/Exporter.pm

[26] - [29] Early work on tree-based structures (k-d trees, R-trees) for metadata queries

[30] TableFS - LSM-tree-based metadata design

[31] - [33] Distributed file system metadata planes

[34] - [35] External metadata indexing systems

[36] Robinhood Policy Engine - https://github.com/cea-hpc/robinhood

[37] QuickSilver - event-driven policy agents

[38] PoliMOR - lifecycle management with scan, policy, and action agents

---

## 2. STELLAR: Storage Tuning Engine Leveraging LLM Autonomous Reasoning

**arXiv:** 2602.23220

[1] Anthropic. Building effective agents, December 2024.

[2] Anthropic. Claude 3.7 Sonnet and Claude Code, February 2025.

[3] Dorian C. Arnold et al. Stack trace analysis for large scale debugging. IPDPS 2007.

[4] Babak Behzad, Surendra Byna, and Marc Snir. Optimizing I/O performance of HPC applications with autotuning. ACM TOPC, 2019.

[5] Jean Luca Bez, Hammad Ather, and Suren Byna. Drishti: Guiding end-users in the I/O optimization journey. PDSW 2022.

[6] Sebastian Borgeaud et al. Improving language model reasoning with self-taught reasoners. 2024.

[18] Lustre stripe_size and stripe_count parameters

[54] Lustre max_rpc_in_flight and max_pages_per_rpc parameters

[35] ASCAR - rule-based I/O tuning

[46] TAPP-IO

[25] DCA-IO

[56] IOPathTune

[40] SAPPHIRE - Bayesian optimization for storage tuning

[4] Behzad et al. - Nonlinear regression and genetic algorithms for I/O

[10] Cao et al.

[55] Rajesh et al.

---

## 3. CARAT: Client-Side Adaptive RPC and Cache Co-Tuning

**arXiv:** 2602.22423

[1] Noah Lewis, Jean Luca Bez, and Surendra Byna. I/O in machine learning applications on HPC systems: A 360-degree survey. ACM Computing Surveys, 2025.

[2] Hammad Ather. Parallel I/O characterization and optimization on large-scale HPC systems. arXiv:2501.00203, 2024.

[3] Jean Luca Bez, Suren Byna, and Shadi Ibrahim. I/O access patterns in HPC applications: A 360-degree survey. ACM Computing Surveys, 56(2):1–41, 2023.

[4] Surendra Byna et al. Parallel I/O, analysis, and visualization of a trillion particle simulation. SC'12.

[5] Laura Clarke et al. The 1000 genomes project: data management and community access. Nature methods, 2012.

[6] Md Hasanur Rashid and Dong Dai. AdapTBF: Decentralized bandwidth control via adaptive token borrowing for HPC storage. IPDPS 2025.

[7] Md Hasanur Rashid et al. IOPathTune: Adaptive online parameter tuning for parallel file system I/O path. arXiv:2301.06622, 2023.

[8] Md Hasanur Rashid et al. DIAL: Decentralized I/O autotuning via learned client-side local metrics. CCGrid 2025.

[9] Chris Egersdoerfer et al. STELLAR: Storage tuning engine leveraging LLM autonomous reasoning. arXiv:2602.23220, 2026.

---

## 4. DIAL: Decentralized I/O AutoTuning via Learned Client-side Local Metrics

**arXiv:** 2602.22392

See CARAT paper [1]-[9] for overlapping references. Additional references from DIAL include work on:
- Decentralized I/O scheduling
- Client-side local metric collection
- Machine learning for storage tuning

---

## 5. AdapTBF: Decentralized Bandwidth Control via Adaptive Token Borrowing

**arXiv:** 2602.22409

[1] Anne Benoit, Thomas Herault, Lucas Perotin, Yves Robert, and Frédéric Vivien. Revisiting I/O bandwidth-sharing strategies for HPC applications. Journal of Parallel and Distributed Computing, 188:104863, 2024.

[2] Peter Braam. The Lustre storage architecture. arXiv preprint arXiv:1903.01955, 2019.

[3] Philip Carns, Kevin Harms, William Allcock, Charles Bacon, Samuel Lang, Robert Latham, and Robert Ross. Understanding and improving computational science storage access through continuous characterization. ACM TOS, 7(3):8, 2011.

[4] Dong Dai, Yong Chen, Dries Kimpe, and Robert Ross. Two-choice randomized dynamic I/O scheduler for object storage systems. SC'14.

[5] Dong Dai, Chen Yong, Philip Carns, John Jenkins, Zhang Wei, and B. Robert Ross. GraphMeta: A graph-based engine for managing large-scale HPC rich metadata. CLUSTER'16.

[6] Dmitry Duplyakin et al. The design and operation of CloudLab. USENIX ATC 19.

[7] Chris Egersdoerfer, Md Hasanur Rashid, Dong Dai, Bo Fang, and Tallent Nathan. Understanding and predicting cross-application I/O interference in HPC storage systems. SC24-W.

[8] Chris Egersdoerfer, Arnav Sareen, Jean Luca Bez, Suren Byna, and Dong Dai. Ion: Navigating the HPC I/O optimization journey using large language models. HotStorage '24.

---

## Common References Across Storage Papers

- **Lustre**: Peter Braam, The Lustre Storage Architecture (arXiv:1903.01955)
- **GPFS**: IBM Spectrum Scale documentation
- **IOR Benchmark**: Standard HPC I/O benchmark
- **DLIO**: Deep Learning I/O benchmark
- **VPIC-IO**: VPIC particle simulation I/O patterns
- **BDCATS**: BDCATS benchmark