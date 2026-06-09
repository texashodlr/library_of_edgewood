# Power Directory

This directory contains papers related to power management, energy efficiency, and power delivery for AI/HPC infrastructure.

## Paper Reviews

---

### 1. Provisioning to Runtime Optimization of a 100 MW-Scale AI Cluster

**Source:** arXiv 2605.24461v2 (May 2026)  
**Authors:** Ehsan K. Ardestani, Leonardo Piga, Jovan Stojkovic, et al. (Meta Platforms)  
**File:** `2605.24461v2.pdf`

#### Summary

This paper presents the first known end-to-end power management process for a hyperscale AI datacenter — from early power planning 6-12 months before next-gen accelerators are generally available, through deployment validation, to dynamic runtime power management. The authors share detailed measurements from a 150 MW datacenter hosting 83K GB200 GPUs connected via RDMA.

Key context: Electric power supply has overtaken accelerator availability as the primary bottleneck in the race toward AGI. US power generation capacity only added 41 GW in 2023→2024, while AI clusters require tens of GW.

#### Key Findings

1. **Power is the primary bottleneck** — Power supply now limits AGI development more than accelerator availability.

2. **Don't use TDP for capacity planning** — Instead of using the accelerator's Thermal Design Power to determine max GPU count, use a lower power limit based on projected power-performance curves to maximize total compute.

3. **Optimal GPU power limit is ~1000W, not max (1200W):**
   - 1200W → 1000W: only 5% performance drop, but 16.7% power savings
   - Allows more GPUs in fixed power envelope
   - **Result: 9% better cluster throughput** vs 1200W

4. **GB200 vs H100 at same 150MW power budget:**
   - GB200 @ 960W: 2.4× per-GPU performance, 1.9× total cluster throughput vs H100
   - GB200 @ 1200W: drops to 1.7× total throughput (less efficient)

5. **Power oversubscription is standard practice** — Datacenters oversubscribe at panel/rack level but must enforce constraints to avoid overload.

6. **Cooling varies seasonally** — Mechanical power demand increases significantly during summer months.

7. **Dynamic runtime tuning required** — Power swings during workloads require active management, not just static provisioning.

#### Actionable Next Steps

- [ ] Review your current GPU power limit settings — consider reducing from max TDP to ~80-85% and measure performance impact
- [ ] Calculate the power-performance curve for your specific GPU workload to find optimal power limit
- [ ] Implement power monitoring across the full hierarchy (MSB → switchboard → panel → rack)
- [ ] Model the power delivery constraints using the methodology in Section 3.1 (Equations 1-5)
- [ ] Plan for oversubscription at lower hierarchy levels but implement enforcement controls
- [ ] Consider seasonal cooling variations in capacity planning
- [ ] Apply the same methodology to AMD GPUs and other accelerator types — the approach is generalizable

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