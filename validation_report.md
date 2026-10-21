# UCSC Assembly Hub validation

Local validation against NC_005881.2 (207,439 bp), performed 2026-10-21.

- 166 unique samples represented (38 Batch 1 + 128 Batch 2); all 1,038 non-overlapping 200-bp windows included, including the 39-bp terminal window.
- Presence matrix counts match the per-window summary. The aggregate count and fraction bigWigs match that summary, and all 166 individual presence bigWigs match their matrix rows.
- The `.2bit` sequence dictionary contains only NC_005881.2 at 207,439 bp. ORF and candidate bigBeds use the same chromosome dictionary; candidate intervals are within bounds.
- Nine candidate genomic FASTA sequences match their NC_005881.2 reference slices; transcript-oriented sequences match the inferred strand orientation.
- All 183 track IDs are unique. All 180 `bigDataUrl` targets resolve locally: 178 bigWigs (166 individual presence, 10 representative coverage, 2 aggregate presence) and 2 bigBeds (ORFs and candidates).
- No FASTQ, BAM, BAI, or host reference files are included. Coverage and presence remain based on existing viral alignments and are not uniformly host-competition-filtered.
- The published GitHub Pages hub, `hub.txt`, `genomes.txt`, `trackDb.txt`, and all 180 referenced bigWig/bigBed URLs were accessible online. Every referenced data URL returned HTTP 200 with an `Accept-Ranges: bytes` header. Range requests to the `.2bit`, aggregate bigWig, candidate bigBed, and representative coverage bigWig returned HTTP 206 with the requested byte ranges.
- UCSC Track Hub Development's online configuration checker reported **0 configuration errors**. UCSC Genome Browser opened the hub on NC_005881.2 and rendered the assembly with the ORF and candidate tracks; representative coverage tracks and aggregate tracks were present in their configured visible groups, while individual presence remained hidden.
- The standalone `hubCheck` binary was unavailable locally. The UCSC online checker validates hub configuration in no-track mode; remote track format and URL availability were additionally checked through local `pybigtools` validation and live HTTP/Range requests.
