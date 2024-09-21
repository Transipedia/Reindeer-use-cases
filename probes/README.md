# Filtered Probe sets for Reindeer queries

Fasta files containing probe sequences for Reindeer queries. Low complexity and multi-hit k-mers were removed as described in [the Reindeer CCLE manuscript](https://doi.org/10.1101/2024.02.27.581927).

* probes_cosmic_mutation.fa: likely oncogenic mutations from the Cosmic V100 [Cancer Mutation Census (CMC)](https://cancer.sanger.ac.uk/cmc/home) tier 1, 2 and 3. Each mutation is represented by 2 probes: alt and ref. Probe length is max. 61nt.

* probes_cosmic_fusion.fa: gene fusions from [Cosmic V100](https://cancer.sanger.ac.uk/cosmic/fusion). Probe length is max 51nt. Probes are restricted to exon-exon fusions. 

* probes_depmap_mutation_50_genes.fa: mutations from the [DepMap Public 22Q2 MAF mutation file](https://depmap.org/portal/), restricted to 50 cancer genes. Each mutation is represented by 2 probes: alt and ref. Probe length is max. 61nt. 

* probes_depmap_fusion.fa: cancer cell line fusions from the [DepMap Public 22Q2 fusion table](https://depmap.org/portal/). Probe length is max 51nt. Probes are restricted to exon-exon fusions. 

