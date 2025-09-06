# Decontamination

## Find hits 

[BLAST](https://blast.ncbi.nlm.nih.gov/Blast.cgi)

```
Altschul, S. F., Gish, W., Miller, W., Myers, E. W., & Lipman, D. J. (1990). Basic local alignment search tool. Journal of Molecular Biology, 215(3), 403-410.
```

![blastn](s3_pic/blastn.png)
![blastn_taxdump](s3_pic/blastn_taxdump.png)

```sh
blastn -query assembly.fasta -db nt -outfmt "6 qseqid staxids bitscore std sscinames scomnames" -max_hsps 1 -evalue 1e-25 -out blast.out
```

## Find BUSCO orthologs

[BUSCO](https://busco.ezlab.org/)

```
Manni, M., Berkeley, M. R., Seppey, M., Simão, F. A., & Zdobnov, E. M. (2021). BUSCO update: novel and streamlined workflows along with broader and deeper phylogenetic coverage for scoring of eukaryotic, prokaryotic, and viral genomes. Molecular Biology and Evolution, 38(10), 4647-4654.
```

```sh
busco --in assembly.fasta --mode genome --out busco_out -l metazoa_odb10
```

## Mapping long reads to the assembly

[minimap2](https://github.com/lh3/minimap2)

```
Li, H. (2018). Minimap2: pairwise alignment for nucleotide sequences. Bioinformatics, 34(18), 3094-3100.
```

![minimap2_hifi](s3_pic/minimap2_hifi_blobtools.png)

```sh
minimap2 -ax map-hifi assembly.fasta hifi_reads.fastq.gz | samtools sort -o minimap2_hifi.bam
minimap2 -ax map-ont assembly.fasta ont_reads.fastq.gz | samtools sort -o minimap2_ont.bam
```

## Create Blobtools directory

[Get new_taxdump.tar.gz here](https://ftp.ncbi.nlm.nih.gov/pub/taxonomy/new_taxdump/)

[Blobtools2](https://github.com/blobtoolkit/blobtoolkit)

```
Challis, R., Richards, E., Rajan, J., Cochrane, G., & Blaxter, M. (2020). BlobToolKit–interactive quality assessment of genome assemblies. G3: Genes, Genomes, Genetics, 10(4), 1361-1374.
```

![blobtools_create](s3_pic/blobtools_create.png)
![blobtools_add](s3_pic/blobtools_add.png)
![blobtools_interactive](s3_pic/blobtools_interactive.png)

```sh
blobtools add --fasta assembly.fasta --cov minimap2_hifi.bam --hits blast.out --busco busco_out/run_metazoa_odb10/full_table.tsv --taxdump taxdump --create blobdir
blobtools view --local blobdir
```
