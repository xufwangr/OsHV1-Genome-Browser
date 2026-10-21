# UCSC Assembly Hub validation

Validation updated 2026-10-21 for reference NC_005881.2 (207,439 bp).

## Coverage heatmaps

- The sample presence matrix contains 166 unique samples. There are 110 samples with at least one positive 200-bp window: ten existing representative high-signal samples retain true-depth bigWig peak graphs, and the other 100 have independent native positional heatmap tracks.
- The three-sample prototype was loaded in the live UCSC Genome Browser before generating the full set. UCSC parsed all three bigBeds and rendered the individual heatmap tracks at the test interval; the prior tooltip-array warning was resolved by correcting the terminal empty-cell encoding. The positive window is visible even in samples with a single positive window; the other windows have empty heatmap cells.
- Each full heatmap bigBed has one sample row, 1,038 genomic columns (1,037 full 200-bp windows and one terminal 39-bp window), and a genome-wide span of 207,439 bp. Its score array contains `log1p(mean per-base depth)` for each window; zero-depth cells are blank. Cell colors progress from pale yellow to dark brown across raw mean-depth bounds 0, 0.01, 0.05, 0.2, 1, 5, 20, 100 and 1,000. The same filters (`samtools depth -aa -Q 30 -q 20`) are used for these BAM-derived depths and the corresponding matrix-positive-window cross-check.
- The 100-sample raw window table has 103,800 rows. For every low-signal sample, the number of nonzero depth windows agrees with its existing 166-sample binary presence row. Depth is per-base depth and can include overlapping mates; it is not a unique read-pair count.
- Existing 166 individual 0/1 presence bigWigs, ten representative coverage bigWigs, two aggregate presence bigWigs, ORF bigBed, and candidate bigBed are retained. No definitive host-competition track is available in this repository, so none was invented or added.

## Existing integration checks retained

- All 1,038 consecutive 200-bp windows, including the final 39 bp, are represented in the aggregate presence statistics.
- The `.2bit` sequence dictionary, ORF bigBed, candidate bigBed, and newly generated heatmap bigBeds all use `NC_005881.2` at 207,439 bp.
- The prior nine candidate FASTA sequences match their NC_005881.2 reference slices and inferred strand orientation. Their mRNA 3′ ends remain unverified predictions/candidates.
- No FASTQ, BAM, BAI, or host reference files are included in the published Hub repository.

## Online validation after deployment

- Commit `e20a439548e490765574e07930257c04eba27a82` is present on `main`. GitHub Pages workflow run #7 completed successfully.
- UCSC Track Hub Development's online configuration checker completed with **0 configuration errors** for the deployed Hub. The `hubCheck` command-line binary was not available locally; the UCSC online checker was used as the equivalent configuration check.
- The published hub definition, genomes file, full 86-kB trackDb, sampled heatmap bigBeds (first, middle and last), representative bigWig and 2bit responded over HTTPS. Range requests to the binary files returned HTTP 206 with the requested bytes. The browser tool returned an empty body for the range request against the text `trackDb.txt`, but a normal GET returned HTTP 200, 86,356 bytes, including all 100 `style heatmap` entries.
- The three-sample prototype had already loaded in UCSC Genome Browser before batch generation and was parsed/rendered without the corrected label-array warning. After deployment, a fresh direct `hgTracks` load resolved the custom assembly title but returned an empty track image/table in the browser session; therefore the complete 100-track set's visual appearance was **not confirmed in a fresh UCSC browser session**. The deployed configuration passes the UCSC online checker, and all sampled data URLs are accessible, but full live rendering remains an outstanding UCSC-side verification.
