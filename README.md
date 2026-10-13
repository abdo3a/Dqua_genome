# Dqua_genome
Desmodesmus quadricauda genome annotation

## Idenfy the exact scpes we sequenced
based recent 48 genomes from 

Li, L., Wang, H., Chen, X. et al. Horizontal gene transfer and diploidy illuminate evolution and stress adaptation in oleaginous Scenedesmaceae (Chlorophyta). Nat Commun 17, 5618 (2026). https://doi.org/10.1038/s41467-026-71696-2

- i used two approach, phylogenmic tree based BUSCO single copy genes and chloroplast protein-marker phylogeny
- 

## Assembling organelle genomes.

I will use [GetOrganelle](https://github.com/Kinggerm/GetOrganelle)



- I build a custom orgnall databases from avaliable organelle genomes from ```https://www.ncbi.nlm.nih.gov/datasets/organelle/?taxon=3086```

````bash
mamba activate assem_env

get_annotated_regions_from_gb.py NC_002254.1.gb NC_036659.1.gb -o scie.cds -t CDS --mix

mv scie.cds/gene/gene.fasta scie_mito.label.fasta

cat NC_002254.1.fasta NC_036659.1.fasta > scie_mito.seed.fasta

get_annotated_regions_from_gb.py Cholor/NC_008101.1.gb Cholor/NC_036668.1.gb Cholor/NC_042181.1.gb Cholor/NC_066651.1.gb Cholor/NC_068582.1.gb Cholor/NC_086752.1.gb Cholor/NC_086753.1.gb Cholor/NC_086754.1.gb Cholor/NC_086755.1.gb Cholor/NC_086756.1.gb -o scie_cp.cds -t CDS --mix
mv scie_cp.cds/gene/gene.fasta scie_cp.label.fasta
````

- Finally, run the analysis

````bash
get_organelle_from_reads.py -s scie_mito.seed.fasta --genes scie_mito.label.fasta -1 Dqu_sr_1.fastq.gz -2 Dqu_sr_2.fastq.gz -o mito_output -R 15 -k 21,45,65,85,105 -t 50 -F anonym

get_organelle_from_reads.py -s scie_cp.seed.fasta --genes scie_cp.label.fasta -1 Dqu_sr_1.fastq.gz -2 Dqu_sr_2.fastq.gz -o cp_output -R 15 -k 21,45,65,85,105 -t 50 -F other_pt

````



## rRNA

./barrnap -q -k euk ../../Desmodesmus_quadricauda.scaffolds.fa --threads 50 --outseq ../../Desmodesmus_quadricauda.rrna.fasta > ../../rrna.gff 

#repeats

