# Reindeer use cases

* use-case 1: [finding mutations](#use-case-1-finding-mutations)
* use-case 2: [finding splice junctions](#use-case-2-finding-splice-junctions)
* use-case 3: [finding chimeras](#Use-case-3-finding-chimeric-junctions)

An increasing number of public RNA-seq datasets is available on the SRA and ENA repositories. This huge body of publicly available RNA-­seq libraries is a treasure of functional information. The objective of the Transipedia project is to provide the scientific community with a new way to obtain insights from NGS data that may deliver results not achievable through traditional means. Organizing large scale data collection is performed with REINDEER, that builds a data-structure that indexes k-mers and their abundances from a collection of raw RNA-seq. The TranSipedia web site then provides an easy way to mine information from these big data.
These use cases demonstrate applications of the server for retrieving different types of events. 

Many additional query probes are provided in the [probes](https://github.com/Transipedia/Reindeer-use-cases/tree/main/probes) subdirectory. 

## Sequence search at Transipedia web site

1. Select one or several indexes.
2. Select the sequence mode: 
	* sequences (probes) can be submitted as input by cut-paste step in a fasta format. 
	* The sequence probes can be kmers of at least 31nt length or longer (see test sequences with Try it), 
	* Users can upload a list of sequences of interest in a fasta file. The maximum size of the query file is 1MB. For bigger datasets, users need to query the index from the command line using [Reindeer](https://github.com/kamimrcht/REINDEER/blob/master/README.md) directly.
3. Select the counting method: **raw** or **normalized** counts (kmer count/total kmers).
4. **Submit** the query.
5. Select the metadata button **More details** when available.

## Use-case 1: finding mutations

1. Copy the probe sequences (fasta formated):

```
>7_140453136_A_T|+|alt
CTCCATCGAGATTTCTCTGTAGCTAGACCAA
>7_140453136_A_T|-|alt
TTGGTCTAGCTACAGAGAAATCTCGATGGAG
>7_140453136_AC_TT|+|alt
CTCCATCGAGATTTCTTTGTAGCTAGACCAA
>7_140453136_AC_TT|-|alt
TTGGTCTAGCTACAAAGAAATCTCGATGGAG
>7_140453137_C_T|+|alt
TCCATCGAGATTTCATTGTAGCTAGACCAAA
>7_140453137_C_T|-|alt
TTTGGTCTAGCTACAATGAAATCTCGATGGA
```

The provided list corresponds to altered/mutated sequences from the BRAF gene. 
The most frequent mutations in the CCLE dataset (V600) were selected from the 
DepMap file  [CCLE_mutations.csv](https://depmap.org/portal/download/all/) 
(release 21Q4). The 31nt kmers were constructed with 
[seqTailor](http://shiva.rockefeller.edu/SeqTailor/) from the vcf information.
    
2. Open the [Transipedia web site](https://transipedia.org).
3. In the **Indexes** area, select **CCLE RNAseq (1019 experiments)**.
4. In the **Request** area, remove the example requests and paste the previously selected requests, click on `Select`.  
    ![request](img/case1-request.png) 
5. optionnally, select the counting method in **Counting method** area.
6. Check your selection in the **Your request** area.
7. Click on **Submit**
8. Select **More details**  at the bottom of the page  
    ![global result](img/case1-global-results.png)
9. Select **Histology** in **group by** box and then **Boxplot**
    ![detailed results](img/case1-details.png)
    You will obtain this graph that confirms the presence of BRAF_V600 mutation mainly observed in Carcinoma and melanoma. 
    You can then check  the kmer specificity on Indexes form normal cells (wt).


## Use-case 2: finding splice junctions

The query sequence here is the 51-nt fragment spanning exon 3-4 junction, specific 
to androgen receptor variant AR-V7 (Gencode transcript AR-204).

This spliced junction is most frequently expressed in PRAD tumors ([https://europepmc.org/article/med/31055861](https://europepmc.org/article/med/31055861)).


1. Copy the the spliced junction fasta sequence below:

```
>AR-204 (AR V7) E3-4
TTATGAAGCAGGGATGACTCTGGGAGAAAAATTCCGGGTTGGCAATTGCAA
```


2. Open the [Transipedia web site](https://transipedia.org).
3. In the **Indexes** area, select CCLE RNAseq.
4. In the **Request** area, remove the example requests and paste the previously selected requests, 
click on **Select**.
5. Optionnally, select the counting method in **Counting method** area.
6. Check your selection in the **Your request** area.
7. Click on **Submit** in **Your request**.
    ![request](img/case2-global-results.png)
8. Select **More details** at the bottom of the page.
9. In **Group By** box, select **tcga_code** and then **Boxplot** in **Plot Type**. You will obtain 
a graph that confirms the presence of BRAF_V600 mutation specifically  observed in PRAD. You can 
then check the kmer specificity on Indexes form normal cells (type **wt** keyword in the index 
search bar).
    ![request](img/case2-details.png)


## Use-case 3: finding chimeric junctions

The fasta sequences below correspond to 31nt fragment covering chimeric junctions. The most frequent chimeric RNA in the **CCLE dataset** (V600) were selected (i) from the DepMap file CCLE_fusion.csv ( release 21Q4), (ii) from **TCGA** ( <https://doi.org/10.1016/j.celrep.2018.03.050>), and (iii) from **LEUCEGENE** (<https://leucegene.ca/research-development/>). 

```
>MLLT3---KMT2A-2
GGACTGGGTTGTTCAGACTTAAAGTCCACTC
>RUNX1---RUNX1T1-3
CCCCGAGAACCTCGAAATCGTACTGAGAAGC
>BCR---ABL1-2
ACCATCAATAAGGAAGAAGCCCTTCAGCGGC
>TMPRSS2---ERG-1
CGCCTGGAGCGCGGCAGGAAGCCTTATCAGT
>SR786|SRR8615372_NPM1--ALK_33
GGACAGCACTTAGTAGTGTACCGCCGGAAGCA
>FGFR3---TACC3-5
CGTGACGTCCACCGACGTAAAGGCGACACAG
>EXOSC10---MTOR
ACAGGTTGCTTCAGTGAAATTTTGGACGGTG
>VTI1A---TCF7L2
AGAAGCGAAAGAACTGTCTAACAAAGTGCCA
>CBFB_MYH11
GGGAGGAAATGGAGGTCCATGAGCTGGAGAA
>PML-RARA
GGCGCCGGGGAGGCAGCCATTGAGACCCAGA
```

1. Copy the list
2. Open the Transipedia web site <https://transipedia.org>. 
3. In the **Indexes** area, select **CCLE RNAseq (1019 experiments)**. 
4. In the **Request** area, remove the example requests and paste the previously selected requests, click on **Select**.
5. Select **counting method** : ex raw counts
6. Check your selection in the Your **request area**.
7. Click on **Submit**
8. Select **More details** at the bottom of the page
9. Select name in **Samples Labels** 
10.  Select **tissue** in **group by** 

One obtains this graph that confirms the presence of the chimeric junctions in specific cell lines. One can then check the kmer specificity on Indexes from normal cells (enter "wt" in the indexes search bar ). 

![request](img/case3-samples-grouped-by-tissues.png)





