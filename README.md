# EMBO 2025 "Genome sequencing, assembly, curation, and downstream analyses"

This is a tutorial on genome assembly prepared for an [EMBO course]([https://meetings.embo.org/event/25-genome-seq), taking place in Florence (Italy) from September 7th to 13th. The tutorial addresses all steps in a genome assembly pipeline of a eukaryote using high-accuracy PacBio HiFi, Nanopore R10.4 long reads and Hi-C. These steps include analyzing long reads prior to assembly, generating the first draft assembly, evaluating the quality of the assembly, purging haplotigs to generate collapsed assemblies, polishing to improve accuracy, removing contigs from contaminants, and Hi-C scaffolding to obtain chromosome-level scaffolds. 

Datasets for this tutorial are available in [Galaxy](https://usegalaxy.eu/u/nguiglie/h/embo2025-assembly). They are a subset of datasets published in European Nucleotide Archive project [PRJEB87118](https://www.ebi.ac.uk/ena/browser/view/PRJEB87118).

## [S1: Analysis of DNA sequencing](https://github.com/nadegeguiglielmoni/EMBO-25-genome-sequencing/blob/main/S1_analysis_dna_sequencing.md)
## [S2: *De novo* assembly](https://github.com/nadegeguiglielmoni/EMBO-25-genome-sequencing/blob/main/S2_de_novo_assembly.md)
## S3: Assembly evaluation, polishing and haplotype purging of the assemblies
* [Assembly evaluation](https://github.com/nadegeguiglielmoni/EMBO-24-genome-sequencing/blob/main/S3_assembly_evaluation.md)
* [Haplotig purging](https://github.com/nadegeguiglielmoni/EMBO-24-genome-sequencing/blob/main/S3_haplotig_purging.md)
* [Polishing](https://github.com/nadegeguiglielmoni/EMBO-24-genome-sequencing/blob/main/S3_polishing.md)
* [Decontamination](https://github.com/nadegeguiglielmoni/EMBO-24-genome-sequencing/blob/main/S3_decontamination.md)
## [S4: Hi-C scaffolding](https://github.com/nadegeguiglielmoni/EMBO-24-genome-sequencing/blob/main/S4_hic_scaffolding.md)

## Other materials

Take a look at these tutorials/scripts if you want to look deeper into genome assembly:
* [Vertebrate Genome Project Galaxy Pipeline](https://training.galaxyproject.org/training-material/topics/assembly/tutorials/vgp_genome_assembly/tutorial.html) : a tutorial for the VGP Galaxy pipeline to easily run your assemblies
* [Nanopore and PacBio HiFi assembly scripts](https://github.com/worm-lab/Revisiting_genomes) for the paper "Revisiting genomes of non-model species with long reads yields new insights into their biology and evolution" that includes extra command lines for genome assembly
* [A review on genome assembly](https://peercommunityjournal.org/articles/10.24072/pcjournal.128/) for non-vertebrate animals that also includes an [exhaustive list of tools for genome assembly](https://github.com/nadegeguiglielmoni/genome_assembly_tools)
