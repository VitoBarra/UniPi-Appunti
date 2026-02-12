---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Software di trimming per RNAseq - Trimmomatic
---
• Strengths – Pipeline-style trimming Combines adapter clipping, sliding-window quality trimming, cropping, length filters, etc., in configurable order. OUP Academic+1 – Reasonably fast & multithreaded Written in Java, performs well and has been a workhorse in many RNA-seq/Illumina pipelines. OUP Academic+1 – Widely supported Built into lots of wrappers/GUI tools and tutorials. • Weaknesses – Slower & less feature-rich than newer “all-in-one” tools fastp, for example, is usually 2–5× faster while also doing QC and more filtering in a single pass. ResearchGate+1 – Adapter logic a bit less flexible Relies on adapter FASTA files and simpler matching; for exotic adapter configurations, Cutadapt/Atropos tend to be more configurable. • Best for: legacy / established pipelines and users who like its simple, modular trimming steps. 