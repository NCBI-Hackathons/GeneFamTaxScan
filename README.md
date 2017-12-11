# GeneFamTaxScan
Scripts for evaluating annotation errors for user-selected gene families, taxonomically delimited.  Uses RefSeq Genomes, RefSeq Proteins as a "Standard Mean Reference" to identify outlying annotation parameters from orthologous non-RefSeq genes of interest.


##
![GeneFamTaxScan](../master/Images/GeneFamTaxScan01.png?sanitize=true)
##

# Steps:

1. Retrieve .csv formatted table of Assembly stats (see [AssemblyStatsFromTaxa.md](../master/AssemblyStatsFromTaxa.md)) -> ([AssemblyStats.csv](../master/AssemblyStats.csv)), Import to R, calculate averages and SDs, readout box-whisker plots.
2. Retrieve .csv formatted table of Protein sequence length (and other stats), calculate averages and SDs, readout box-whisker plots (see [ProtSlenFromGeneID.md](../master/ProtSlenFromGeneID.md)) -> ([ProtSlen.csv](../master/ProtSlen.csv))
  * Make a comparative report - between and within taxon parent groups, RefSeq vs non-RefSeqs. (see R script [AssemblyStatsCompare.R](../master/AssemblyStatsCompare.R), and prelim Boxplots [AssemblyStatsGraphs.md](../master/AssemblyStatsGraphs.md))
3. Retrieve Gene(DNA) .fasta given a Homologene ID using Assembly-associated chr_start,chr_stop positions. (use [homolog2fasta.sh](../master/homolog2fasta.sh))
4. Retrieve Protein .fasta given GeneIDs associated with RefSeq genome. (use [ProtFastaFromGene.sh](../master/ProtFastaFromGene.sh))
5. Retrieve RefSeq Assembly .gz files for taxa of interest. (see [RefSeqAssemblyFastaByTax.md](../master/RefSeqAssemblyFastaByTax.md))
6. Make BLAST databases from Gene .fastas, RefSeq Protein .fastas, RefSeq Assembly .gz.
7. Retrieve *Non-RefSeq* Genome, Protein accessions from Taxonomy subset of interest.  Compare meta-stats to "Reference" sequence SD values, find sequences outside Reference ranges, or with divergent BLAST results. 
  * Retrieve child taxa from a parent node using ETE3 (use [ChildTaxaByParent.py](../master/ChildTaxaByParent.py)).
