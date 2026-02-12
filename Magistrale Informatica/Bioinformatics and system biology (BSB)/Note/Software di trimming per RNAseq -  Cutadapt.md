---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Software di trimming per RNAseq - Cutadapt
---
Strengths – Extremely flexible adapter handling Supports 5'/3' adapters, anchored adapters, linked adapters, variable-length adapters, overlapping modes, etc. cutadapt.readthedocs.io+1 – High trimming accuracy Benchmarks generally show very good sensitivity for removing true adapter sequence. PMC+1 – Mature & well documented Long history, excellent docs, widely used, lots of community examples. cutadapt.readthedocs.io+1 • Weaknesses – Not the fastest Historically slower than newer C++ tools (e.g. fastp) and often slower than BBDuk/Trimmomatic in speed-focused benchmarks. ResearchGate+1 – Narrow scope It focuses on trimming; QC plots, advanced filtering, UMIs, etc. need other tools or extra scripting. • Best for: maximum control over adapter trimming logic and “weird” adapter setups