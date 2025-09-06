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
