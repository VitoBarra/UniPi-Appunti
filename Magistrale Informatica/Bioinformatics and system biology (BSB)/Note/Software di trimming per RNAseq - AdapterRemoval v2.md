---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Software di trimming per RNAseq - AdapterRemoval v2
---
• Strengths – Outstanding for overlapping paired-end reads Very high merge rate and speed; top of the pack for merging in multiple benchmarks, especially useful for short inserts / degraded DNA (e.g. ancient DNA). BioMed Central+2PMC+2 – Rich adapter-related features Handles multiple adapter pairs in the same dataset, simultaneous demultiplexing+trimming, and can reconstruct unknown adapters from overlapping pairs. BioMed Central+1 – High throughput Uses SIMD and multithreading; among the fastest trimmers in several tests. Research Profiles+1 • Weaknesses – Focused tool, fewer extras No built-in HTML QC reports, fancy visualizations, etc. (you’ll typically still run FastQC or multiQC separately). – Not always the very fastest for pure trimming For datasets with multiple adapters but no merging, AlienTrimmer and Trimmomatic edged it out in some benchmarks. BioMed Central • Best for: short/degraded libraries and projects where merging paired-end reads is central.