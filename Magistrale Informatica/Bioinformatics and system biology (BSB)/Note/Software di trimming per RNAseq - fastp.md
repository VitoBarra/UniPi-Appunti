---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Software di trimming per RNAseq - fastp
---
• Strengths – Very fast C++ with multithreading; typically 2–5× faster than Trimmomatic or Cutadapt in authors’ benchmarks, despite doing more work per read. PubMed+2ResearchGate+2 – All-in-one preprocessor Adapter trimming (auto-detection or specified), quality filtering, per-read pruning, polyG/polyX trimming, low-complexity filtering, UMI handling, base correction for PE, output splitting, etc., all in a single pass. SciSpace+2Semantic Scholar+2 – Built-in QC Generates JSON/HTML reports with per-base quality, content, duplication, etc., so you often don’t need a separate FastQC run. BioRxiv+1 – Easy deployment Single executable, widely packaged. • Weaknesses – Less “surgical” adapter configuration Cutadapt/Atropos still offer more specialised adapter matching modes; fastp’s adapter handling is powerful but more automatic and less fine-grained for edge-case designs. cutadapt.readthedocs.io+1 – Heavy reliance on defaults Because it does so much automatically, it’s easy to over-trim / over-filter if you don’t read the docs and QC report carefully. • Best for: fast, convenient “one command” preprocessing + QC, especially for standard Illumina short-read data. 