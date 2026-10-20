# OsHV-1 UCSC Genome Browser Hub

## Overview
This hub visualizes OsHV-1 whole-genome transcriptional profiling across 38 oyster developmental stages.

## Files Included
```
ucsc_hub/
├── hub.txt                      # Main hub configuration
├── genomes.txt                  # Genome assembly definition  
├── trackDb.txt                  # All track definitions (645 lines)
├── description.html             # Hub description webpage
├── README.md                    # This file
├── coverage_*.bedGraph          # 38 sample coverage tracks
├── cds_annotation.bed           # CDS gene annotation
├── cds_primers_priority.bed     # Priority PCR primer targets
├── intergenic_candidates.bed    # Intergenic transcription candidates
├── intergenic_primers.bed       # Intergenic region primers
├── low_activity_windows.bed     # Low-activity transcription windows
├── persistent_windows.bed       # Persistent transcription regions (0 detected)
└── top_genes.bed                # Top 20 highly expressed genes
```

## How to Load This Hub

### Option 1: Local File (for testing)
1. Copy the entire `ucsc_hub/` folder to a web server
2. Note the full URL to `hub.txt`
3. In UCSC Genome Browser: Hubs → Load Hub → enter URL

### Option 2: Share with Others
Upload to a web-accessible location:
- University web server
- GitHub Pages
- Dropbox (with direct link)
- AWS S3 bucket

Example URL format:
```
https://your-server.com/path/to/ucsc_hub/hub.txt
```

## UCSC Genome Browser Usage

1. Go to: https://genome.ucsc.edu/cgi-bin/hgGateway
2. Click "Hubs" tab (or "My Hubs" button)
3. Enter the hub URL
4. Click "Submit" or "Add Hub"

## Track Information

### Coverage Tracks (oshvCoverage)
Shows RNA-seq read depth across the viral genome for each sample.
- **38 samples** ordered by developmental stage
- **Color coding** based on viral transcription activity:
  - 🔴 Red: Widespread transcription (>100 viral reads, >20% genome coverage)
  - 🟡 Yellow: Localized transcription (20+ viral reads)
  - 🟢 Light Green: Sparse, below detection gate
  - 🟢 Dark Green: Undetected after host screening

### Genomic Features (oshvDescription)
- CDS annotation from NCBI NC_005881.2

### Candidate Regions (oshvCandidates)
- **Persistent regions** (black): Detected in ALL detectable samples
- **Low-activity candidates** (orange): Regions in low viral load samples
- **Intergenic candidates** (purple): Potential non-coding transcription

### PCR Primer Targets (oshvPrimers)
- **CDS Primers** (green): Top 50 priority targets in CDS
- **Intergenic Primers** (purple): Targets in intergenic regions

### Top Expressed Genes (oshvTopGenes)
- Top 20 most highly expressed CDS

## Sample Order (Developmental Stages)
```
1-2:   E, TC         - Early oocyte / transcription start
3-6:   EM, M, B, RM  - Embryo
7-14:  FS, EG, G, T1-T5 - Trochophore larvae
15-23: ED1-2, D1-D7  - Early D-type larvae  
24-25: EU1, EU2      - Early umami (viral increase begins)
26-31: U1-U6         - Umami larvae (PEAK viral activity)
32-33: LU1, LU2      - Late umami (viral decline)
34-36: P1, P2, S     - Post-settlement (second peak)
37:    J             - Juvenile (return to low)
```

## Data Source
- Reference: NCBI NC_005881.2 (207,439 bp)
- Analysis: Automated RNA-seq bioinformatics pipeline
- Host screening: Oyster genome v9

## Contact
See main analysis report for methodology details.