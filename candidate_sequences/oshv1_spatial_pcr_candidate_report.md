# OsHV-1 空间转录组 PCR 候选区域（序列筛选，不含引物）

参考：NC_005881.2，长度 207,439 bp。候选序列取自各 ORF 注释链的编码末端约 600 bp 区间，优先选择 200 bp 窗口中跨样品反复出现的覆盖；该区间只是便于后续靶向设计的参考片段，不代表真实 mRNA 3′ 端。

现有注释没有已验证的病毒转录本 3′ 端或 poly(A) 位点，RNA-seq 也非链特异。因此所有候选均为 Tier 3 探索性候选，转录方向仅按 ORF 注释推测。Batch2 有更新宿主参考竞争比对记录，但 Batch1 未按该版本筛查；宿主歧义尚未对两批统一评估。重复和低可比对风险仅依据现有参考注释/窗口标记。

| Candidate | ORF | Coordinate (1-based inclusive) | Strand inference | Length | GC% | Positive samples/166 | Repeat | Mappability | Tier |
|---|---|---:|:---:|---:|---:|---:|---|---|---|
| SPC01 | OsHV1_gp099 | 166301-166700 | + | 400 | 48.00 | 36/166 (0.216867) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |
| SPC02 | OsHV1_gp083 | 136701-136934 | - | 234 | 42.31 | 33/166 (0.198795) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |
| SPC03 | OsHV1_gp097 | 160901-161300 | + | 400 | 41.00 | 34/166 (0.204819) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |
| SPC04 | OsHV1_gp073 | 126701-127038 | + | 338 | 38.46 | 32/166 (0.192771) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |
| SPC05 | OsHV1_gp075 | 128041-128300 | + | 260 | 42.31 | 31/166 (0.186747) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |
| SPC06 | OsHV1_gp026 | 42642-42900 | - | 259 | 39.00 | 29/166 (0.174699) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |
| SPC07 | OsHV1_gp066 | 112301-112700 | + | 400 | 39.50 | 29/166 (0.174699) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |
| SPC08 | OsHV1_gp105 | 174285-174500 | + | 216 | 40.28 | 28/166 (0.168675) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |
| SPC09 | OsHV1_gp093 | 149601-149800 | + | 200 | 39.00 | 81/166 (0.487952) | Low based on annotated repeats | No low-mappability flag in available 200 bp track | Tier 3 |

候选阳性率是样品是否至少一个 qualifying read 覆盖候选区间的比例，不是表达量。FASTA 中 genomic 文件输出参考正链，transcript-oriented 文件按 CDS 注释方向输出；方向尚未由链特异数据验证。

暂定后续验证顺序可优先考虑 SPC01–SPC05：它们是覆盖反复检出的 ORF 编码末端附近片段，且在当前已注释 repeats/低可比对标记中未见明显风险；这只是候选排序，不能替代宿主交叉比对和转录本末端验证。SPC09 位于 OsHV1_gp093（DNA polymerase）内部，是全基因组窗口阳性频率最高的覆盖热点（81/166），但离注释 CDS 3′ 端较远，因此作为覆盖热点对照，不优先用于 poly(dT) 端锚定扩增。
