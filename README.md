# Dqua_genome
Desmodesmus quadricauda genome annotation

Assembling organelle genomes.
I will use [GetOrganelle](https://github.com/Kinggerm/GetOrganelle)


if the assembly graph file is not available, then you need to convert it from the assembly file (.fasta)

gfastats ../Results/Assembly/aip_flye_raw/assembly.fasta -o gfa > Aip.contigs.gfa

we build a custom orgnall databases from avaliable organelle genomes from https://www.ncbi.nlm.nih.gov/datasets/organelle/?taxon=3086

mamba activate assem_env
get_organelle_config.py --add  animal_mt
Running time: 2m41,742s

Finally, run the analysis
get_organelle_from_assembly.py -F animal_mt -g ../Results/Assembly/Aip.contigs.gfa -o animal_mt_out
Exercise: visualize animal_mt_out/slimmed_assembly_graph.gfa and load animal_mt_out/slimmed_assembly_graph.csv to confirm the incomplete result.



#rRNA
./barrnap -q -k euk ../../Desmodesmus_quadricauda.scaffolds.fa --threads 50 --outseq ../../Desmodesmus_quadricauda.rrna.fasta > ../../rrna.gff 

#repeats

