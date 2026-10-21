# OsHV-1 UCSC Assembly Hub

This repository publishes an Assembly Hub for exploring OsHV-1 RNA-seq mapping across 166 oyster samples (38 in Batch 1 and 128 in Batch 2), with ORF annotation, sample-level coverage, cross-sample window presence, and spatial-transcriptomics PCR candidate regions.

## Reference and access

- Reference: Ostreid herpesvirus 1, **NC_005881.2**, assembly GCF_000846065.1, 207,439 bp.
- Hub: <https://xufwangr.github.io/OsHV1-Genome-Browser/hub.txt>
- Browser: open UCSC Genome Browser → **My Data** → **Track Hubs** → **My Hubs**, then add the Hub URL above.

## Track groups

- **OsHV-1 overview**: 127 annotated CDS/ORFs, 166-sample 200-bp positive-sample count and fraction, and nine exploratory spatial PCR candidates.
- **High-abundance coverage tracks**: ten representative samples (five from each batch) as true per-base-depth bigWig peak graphs. These are raw-virus alignments filtered by `samtools depth -aa -Q 30 -q 20`; they are not binary presence tracks.
- **Low-abundance heatmaps**: one independent native UCSC positional-heatmap track for each of the other 100 positive samples. Each row spans the genome in non-overlapping 200-bp windows. A positive cell fills the heatmap row at that x position; an empty cell has no qualifying coverage. The display uses log1p(mean per-base depth), with depth bounds 0, 0.01, 0.05, 0.2, 1, 5, 20, 100 and 1,000 mapped to a pale-yellow-to-dark-brown gradient. Thus any nonzero depth is colored, while greater average depth is darker. Tooltips and the raw values table retain mean depth, covered bases, and maximum depth.
- **Individual presence**: the existing 166-sample 0/1 bigWig tracks are retained hidden by default for provenance and quick binary lookup.

The low-abundance heatmap and high-abundance coverage tracks together represent all 110 samples with at least one qualifying 200-bp window. Ten samples use true-depth bigWigs and 100 use heatmaps; samples with no positive windows are not assigned an individual mapping track. The heatmap is a depth visualization, not a read-pair count. Per-base depth can include overlapping mates from the same pair.

The 166-sample **positive count** track reports the number of samples with at least one qualifying covered base in a window (0–166); it is not the number of reads. **Positive fraction** is that count divided by 166; it is not expression abundance. The binary presence definition is one or more covered bases with nonzero depth under `samtools depth -aa -Q 30 -q 20`, counted at most once per sample and window.

## Data and limitations

Presence statistics combine existing viral alignments from both batches using the same window-level rule; no FASTQ remapping was performed. The combined tracks are not uniformly host-competition-filtered virus-specific reads: Batch 1 was not screened against the updated oyster reference, and Batch 2 competition results were not mixed into this presence set. Viral mapping or coverage alone does not establish active replication, transcription direction, or absolute RNA abundance. The RNA-seq libraries are not uniformly strand-specific.

Spatial PCR candidate TSV, genomic plus-strand FASTA, transcript-oriented FASTA, and evidence report are in [`candidate_sequences/`](./candidate_sequences/). The nine candidates are exploratory Tier 3 regions; their mRNA 3′ ends and poly(A) sites have not been experimentally validated. These sequences are reference slices, not primer designs. Host cross-mapping has not been assessed uniformly across all samples.

Raw per-window depth values and the sample-to-track mapping are published in [`heatmap/low_abundance_coverage_windows_200bp.tsv`](./heatmap/low_abundance_coverage_windows_200bp.tsv) and [`heatmap/low_abundance_tracks.tsv`](./heatmap/low_abundance_tracks.tsv). Other integration tables are in [`results/`](./results/).

Analysis and Hub update date: **2026-10-21**. FASTQ, BAM, and BAI files are not included in this repository.
