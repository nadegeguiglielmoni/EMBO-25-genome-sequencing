# Assembly evaluation

## Assembly statistics

[gfastats](https://github.com/vgl-hub/gfastats)

```
Formenti, G., Abueg, L., Brajuka, A., Brajuka, N., Gallardo-Alba, C., Giani, A., ... & Jarvis, E. D. (2022). Gfastats: conversion, evaluation and manipulation of genome sequences using assembly graphs. Bioinformatics, 38(17), 4214-4216.
```

![gfastats](s3_pic/gfastats.png)

```sh
gfastats assembly.fasta --nstar-report --locale en_US.UTF-8  --tabular 
```

```
# scaffolds 	166
Total scaffold length 	43,567,352
Average scaffold length 	262,453.93
Scaffold N50 	941,457
Scaffold auN 	3,479,015.56
Scaffold L50 	7
Largest scaffold 	8,189,580
Smallest scaffold 	599
# contigs 	211
Total contig length 	43,567,352
Average contig length 	206,480.34
Contig N50 	753,921
Contig auN 	3,234,472.34
Contig L50 	8
Largest contig 	8,082,680
Smallest contig 	599
# gaps in scaffolds 	0
Total gap length in scaffolds 	0
Average gap length in scaffolds 	0.00
Gap N50 in scaffolds 	0
Gap auN in scaffolds 	0.00
Gap L50 in scaffolds 	0
Largest gap in scaffolds 	0
Smallest gap in scaffolds 	0
Base composition (A:C:G:T) 	12,626,844:9,114,077:9,142,553:12,683,878
GC content % 	41.90
# soft-masked bases 	0
# segments 	166
Total segment length 	35,279,172
Average segment length 	212,525.13
# gaps 	0
# paths 	166
# edges 	75
Average degree 	0.45
# connected components 	3
Largest connected component length 	33,114,098
# dead ends 	220
# disconnected components 	109
Total length disconnected components 	2,131,845
# separated components 	112
# bubbles 	1
# circular segments 	3
# circular paths 	3
Scaffold N10 	8,189,580
Scaffold N20 	8,067,949
Scaffold N30 	8,067,949
Scaffold N40 	1,661,934
Scaffold N50 	941,457
Scaffold N60 	835,646
Scaffold N70 	685,218
Scaffold N80 	506,658
Scaffold N90 	231,096
Scaffold N100 	599
Scaffold L10 	1
Scaffold L20 	2
Scaffold L30 	2
Scaffold L40 	3
Scaffold L50 	7
Scaffold L60 	12
Scaffold L70 	17
Scaffold L80 	25
Scaffold L90 	37
Scaffold L100 	166
Contig N10 	8,082,680
Contig N20 	7,938,813
Contig N30 	7,938,813
Contig N40 	1,469,920
Contig N50 	753,921
Contig N60 	506,658
Contig N70 	295,207
Contig N80 	207,459
Contig N90 	106,900
Contig N100 	599
Contig L10 	1
Contig L20 	2
Contig L30 	2
Contig L40 	3
Contig L50 	8
Contig L60 	16
Contig L70 	28
Contig L80 	46
Contig L90 	72
Contig L100 	211
Gap N10 	0
Gap N20 	0
Gap N30 	0
Gap N40 	0
Gap N50 	0
Gap N60 	0
Gap N70 	0
Gap N80 	0
Gap N90 	0
Gap N100 	0
Gap L10 	0
Gap L20 	0
Gap L30 	0
Gap L40 	0
Gap L50 	0
Gap L60 	0
Gap L70 	0
Gap L80 	0
Gap L90 	0
Gap L100 	0 
```

Here there are 166 scaffolds, with a total assembly size of 43,567,352 bases. This is larger than the expected genome size for the two haplotypes of chromosome E.

## Ortholog completeness

To learn more [about BUSCO](https://www.youtube.com/watch?v=Q0T4DLGFSNQ&t=3s)

[BUSCO](https://busco.ezlab.org/)

```
Manni, M., Berkeley, M. R., Seppey, M., Simão, F. A., & Zdobnov, E. M. (2021). BUSCO update: novel and streamlined workflows along with broader and deeper phylogenetic coverage for scoring of eukaryotic, prokaryotic, and viral genomes. Molecular biology and evolution, 38(10), 4647-4654.
```

![busco](s3_pic/busco.png)

```sh
busco --in assembly.fasta --mode genome --out busco_out --evalue 0.001 --limit 3 --contig_break 10 --auto-lineage
```

There are several outputs, including a full table of orthologs, and a short summary with statistics.

```
# BUSCO version is: 5.5.0 
# The lineage dataset is: eukaryota_odb10 (Creation date: 2024-01-08, number of genomes: 70, number of BUSCOs: 255)
# Summarized benchmarking in BUSCO notation for file /data/dnb11/galaxy_db/files/7/9/3/dataset_793fa9a7-b2df-454f-b384-d42a90a1d21c.dat
# BUSCO was run in mode: euk_genome_met
# Gene predictor used: metaeuk

	***** Results: *****

	C:10.2%[S:1.2%,D:9.0%],F:0.8%,M:89.0%,n:255	   
	26	Complete BUSCOs (C)			   
	3	Complete and single-copy BUSCOs (S)	   
	23	Complete and duplicated BUSCOs (D)	   
	2	Fragmented BUSCOs (F)			   
	227	Missing BUSCOs (M)			   
	255	Total BUSCO groups searched		   

Assembly Statistics:
	30	Number of scaffolds
	30	Number of contigs
	35951546	Total length
	0.000%	Percent gaps
	2 MB	Scaffold N50
	2 MB	Contigs N50


Dependencies and versions:
	hmmsearch: 3.1
	bbtools: 39.01
	prodigal: 2.6.3
	busco: 5.5.0
	metaeuk: 6.a5d39d9
```

The Eukaryota lineage was selected automatically. Among 255 orthologs, 26 were found as complete in the assembly, 3 in single copy, and 23 duplicated. The high proportion of duplicated orthologs is expected, as we have a phased assembly where both copies of the chromosome, thus both alleles of the genes, are included in the assembly. Therefore the orthologs are expected in two copies. The BUSCO score here is low for two reasons: the lineage is rather large (Eukaryota) and we are only assembling one chromosome (in two copies), not the whole genome. 

## *k*-mer completeness

To learn more [about Merqury](https://www.youtube.com/watch?v=F2wsXEnMP0U)

```
Rhie, A., Walenz, B. P., Koren, S., & Phillippy, A. M. (2020). Merqury: reference-free quality, completeness, and phasing assessment for genome assemblies. Genome biology, 21(1), 245.
```

[Meryl](https://github.com/marbl/meryl)
[Merqury](https://github.com/marbl/merqury)

![meryl](s3_pic/meryl.png)

![merqury](s3_pic/merqury.png)

# Quality control metrics for the contigs generated from Hifiasm with HiFi+ONT (decontaminated)

## Merqury
Spectra-CN plot (fl) for the primary assembly
![contigs_merqury](s3_pic/contigs_merqury.png)
**NOTE:** the default Merqury plot rendering is zoomed in, to zoom out you need to download the histogram file and run the [plot_spectra.R](https://github.com/marbl/merqury/blob/master/plot/plot_spectra_cn.R) script.

## BUSCO
Metazoa BUSCO set:
![busco_contigs_metazoa](s3_pic/busco_contigs_metazoa.png)
Nematoda BUSCO set:
![busco_contigs_nematoda](s3_pic/busco_contigs_nematoda.png)
