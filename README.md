# OsHV-1 UCSC Assembly Hub

## Project and reference

This Assembly Hub displays viral RNA-seq mapping coverage and 200-bp sample-level read presence for 166 oyster samples (38 from Batch 1 and 128 from Batch 2), plus exploratory spatial-transcriptomics PCR target regions. The reference is **Ostreid herpesvirus 1 NC_005881.2**, assembly GCF_000846065.1, length 207,439 bp.

Hub URL: <https://xufwangr.github.io/OsHV1-Genome-Browser/hub.txt>

## Load in UCSC Genome Browser

Open the hub URL in the UCSC Genome Browser through **My Data → Track Hubs → My Hubs → Add**. The landing page also links to the browser with this assembly selected.

## Tracks

- **OsHV-1 ORFs**: 127 NCBI annotated CDS/ORFs, with the annotated strand and coordinates.
- **Representative coverage**: ten representative samples selected using viral alignment signal and breadth, with raw depth bigWigs. Coverage values are not binarized. The input was existing viral alignment/depth data filtered at MAPQ ≥30 and base quality ≥20.
- **Positive n**: for each 200-bp window, the number of samples (0–166) with at least one qualifying aligned base.
- **Positive fraction**: positive samples divided by the 166 valid samples (0–1).
- **Spatial PCR candidates**: nine exploratory Tier 3 regions. Candidate IDs, ORF, inferred strand, 3′-end evidence and host-risk limitations appear in item labels and linked files.
- **Individual presence**: 166 0/1 sample tracks, hidden by default; their order follows the input order within Batch 1 and Batch 2.

Presence means a window has at least one base with nonzero depth under `samtools depth -aa -Q 30 -q 20`. Multiple reads or mates in the same sample-window contribute only one positive. Presence count is **not reads per window**, and presence fraction is **not expression abundance**.

## Comparability and limitations

The two batches were combined using this common binary window-presence definition, based on existing viral alignment outputs; no FASTQ remapping was done. This is **not a uniformly host-competition-filtered virus-specific dataset**: Batch 1 was not screened with the updated host reference, and Batch 2 host-competition results are not merged into this presence set. Viral alignment or coverage does not by itself establish transcription direction, active replication, or absolute RNA abundance. The source reads are not uniformly strand-specific.

Candidate files are in [`candidate_sequences/`](./candidate_sequences/): [TSV](./candidate_sequences/oshv1_spatial_pcr_candidates.tsv), [genomic plus-strand FASTA](./candidate_sequences/oshv1_spatial_pcr_candidates_genomic.fasta), [transcript-oriented FASTA](./candidate_sequences/oshv1_spatial_pcr_candidates_transcript_oriented.fasta), and [evidence report](./candidate_sequences/oshv1_spatial_pcr_candidate_report.md). Candidate mRNA 3′ ends and poly(A) sites have **not** been experimentally validated; FASTA sequences are reference slices, not primer designs. Host cross-mapping risk has not been evaluated uniformly across all 166 samples. Competition-related tracks are therefore not presented as definitive host-vs-virus classifications.

Tabular 166-sample outputs are in [`results/`](./results/): sample metadata, per-sample viral statistics, the 166 × 1,038 binary presence matrix, per-window positive count/fraction summary, integration QC JSON, and the representative coverage sample list. These presence/statistics files inherit the same unfiltered raw-virus alignment caveat.

Analysis and hub files last prepared: 2026-10-21. No FASTQ, BAM, or BAI files are included.
