---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Software di trimming per RNAseq - Atropos
---
 Strengths – High accuracy + speed The Atropos paper reports up to ~4× higher trimming accuracy and ~50% lower runtime than other state-of-the-art trimmers using 16 threads. PMC+1 – Cutadapt DNA with extra muscles It’s a fork of Cutadapt, so you get its flexible adapter specification plus added features (better multithreading, additional algorithms, error modeling). PMC+1 – Advanced options Support for bisulfite data, various quality-trimming strategies, etc., targeting modern high- volume sequencing experiments. PMC+1 • Weaknesses – Smaller user base Less “standard” than Trimmomatic/Cutadapt/fastp, so fewer tutorials, wrappers and example pipelines. – Python-based install Heavier environment than a single static binary (like fastp), which can be mildly annoying on some HPC setups. • Best for: users who love Cutadapt’s flexibility but want better speed and extra advanced trimming modes