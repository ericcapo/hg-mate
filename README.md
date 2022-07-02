# Hg-MATE-Db: Hg-cycling Microorganisms in Aquatic and Terrestrial Ecosystems Database
<p align="justify">
Microorganisms play a significant role in regulating the form and fate of mercury (Hg) in aquatic and terrestrial ecosystems. Microbes with the hgcAB gene pair can produce a more toxic, and bioaccumulative form of Hg, methylmercury (MeHg). Microbes that possess the mer operon can demethylate and/or reduce Hg species as part of a detoxification mechanism. Improved techniques for capturing hgcAB and mer presence and diversity are necessary for identifying the major microbial players in environmental Hg cycling. The primary goal of the database Hg-MATE is to provide an up-to-date collated resource of Hg-cycling genes from pure culture and environmental microbial genomes and meta-omic datasets. The current <b>version 1</b> contains an hgcAB dataset with resources for identifying key microbial producers of the toxin MeHg. Future versions  will include a mer gene dataset, which will contain resources for identifying genes of the mer-operon that encode for demethylation of organomercurials (merB), reduction of inorganic Hg(II) (merA), as well as operon regulation (merR), and Hg transport across the cell (merTPC).
</p>

## Resources
<p align="justify">
The Hg-MATE database v1.01142021 contains:
* <b> A catalogue of 1053 HgcAB amino acid sequences </b>. There, HgcAB amino acid sequences are categorized into four types depending on whether they were encoded in pure culture/environmental microbial isolates (<i>ISO</i>), single-cell genome sequences (<i>CEL</i>), metagenome-assembled genomes (<i>MAGs</i>) and environmental meta-omic contig (<i>CON</i>). Included in the database are amino acid sequences of HgcA, HgcB, and concatenated HgcA and HgcB. If hgcB is not co-localized with hgcA in the genome and/or cannot be identified, then ‘na’ will be listed in the ‘HgcB’ sequence column. We collated the HgcAB databases from <a href="https://doi.org/10.3389/fmicb.2020.541554" target="_blank"><b>Gionfriddo et al. 2020</b></a> and <a href="https://doi.org/10.1128/mSystems.00299-20" target="_blank"><b>McDaniel et al. 2020</b></a> and added HgcAB amino acid sequences pulled from three public data repositories: <a href="https://www.ncbi.nlm.nih.gov/genbank/" target="_blank"><b>NCBI GenBank</b></a>, <a href="https://gold.jgi.doe.gov/" target="_blank"><b>JGI-IMG GOLD</b></a> and <a href="https://gtdb.ecogenomic.org/" target="_blank"><b>GTDB release 89</b></a> obtained on 23 October 2020. HgcAB amino acid sequences were identified in these databases by hmmsearch with HgcA and HgcB HMM profiles from <a href="https://doi.org/10.3389/fmicb.2020.541554" target="_blank"><b>Gionfriddo et al. 2020</b></a>. Other resources generated from pure culture/environmental isolates, single-cell genome sequences, and metagenome-assembled genomes (‘ISOCELMAG’) include 
* <b>FASTA files </b> containing amino acid sequences of HgcA (‘_HgcA.fas’), HgcB (‘_HgcB.fas’), and concatenated HgcA-HgcB sequences (‘_Hgc.fas’). FASTA files with either unaligned and aligned (msa) amino acid sequences are provided.
* <b>Hidden Markov models</b> containing amino acid sequences of HgcA (‘_HgcA.hmm’), HgcB (‘_HgcB.hmm’), and concatenated HgcA-HgcB sequences (‘_Hgc.hmm’). These HMM profiles can be used to detect homologs of hgc genes in meta-omics dataset.
* <b>Reference packages</b> that can be used to identify and classify: 1) the cap-helix encoding region of HgcA (‘_HgcA_CH.refpkg‘), for example in Desulfovibrio desulfuricans ND132, this encompasses the CdhD-like encoding region, sites ~37-156 of HgcA (https://www.uniprot.org/uniprot/F0JBF0); 2) full HgcA (‘_HgcA_Full.refpkg‘); and 3) concatenated HgcA and HgcB (‘_HgcA-HgcB.refpkg‘). Each reference package contains sequence alignments, HMM model, phylogenetic tree, and NCBI taxonomy.
</p>


## Recommended Usage
<p align="justify">
  We recommend using the resources provided by Hg-MATE (HMM profiles and reference packages) to detect and taxonomically identify hgcAB genes in metagenomes, metatranscriptomes and MAGs. The detection, counting and taxonomic identification of hgcAB genes can be done from raw fastq files with <a href="https://academic.oup.com/bioinformatics/article/34/17/i884/5093234" target="_blank"><b>marky-coco</b></a> introduced in <a href="https://www.biorxiv.org/content/10.1101/2022.03.14.484253v1.abstract" target="_blank"><b>Capo et al. 2022</b></a>. Briefly, the metagenomes are trimmed and cleaned using <a href="https://academic.oup.com/bioinformatics/article/34/17/i884/5093234" target="_blank"><b>fastp</b></a> (Chen et al. 2018) with following parameters: -q 30 -l 25 --detect_adapter_for_pe --trim_poly_g --trim_poly_x. A de novo single assembly approach is applied using the assembler <a href="https://github.com/voutcn/megahit" target="_blank"><b>megahit</b></a> 1.1.2 (Li et al 2016) with default settings. The annotation of the contigs for prokaryotic protein-coding gene prediction is done with the software <a href="https://github.com/hyattpd/Prodigal" target="_blank"><b>prodigal</b></a> 2.6.3 (Hyatt et al 2010) (Hyatt et al., 2010). The DNA reads are mapped against the contigs with <a href="http://bowtie-bio.sourceforge.net/bowtie2/manual.shtml" target="_blank"><b>bowtie2</b></a> (Langdmead and Salzberg 2012), and the resulting .sam files are converted to .bam files using <a href="http://www.htslib.org/" target="_blank"><b>samtools</b></a> 1.9 (Li et al 2009). The .bam files and the prodigal output .gff file are used to estimate read counts by using <a href="https://rnnh.github.io/bioinfo-notebook/docs/featureCounts.html" target="_blank"><b>featureCounts</b></a>  (Liao et al 2014). Then, hgcAB homologs are detected and taxonomically identified using the in-house script genesearch.sh associated to HMM profiles and the reference package ‘hgcA’ from the database Hg-MATE version 1.
</p>

## Contributors
<p align="justify">
The Hg-MATE v1.01142021 was primarily compiled by Caitlin Gionfriddo (Smithsonian Environmental Research Center, USA), Eric Capo (ICM-CSIC, Barcelona, Spain), and Benjamin Peterson (University of Wisconsin-Madison, USA), with contributions from Heyu Lin (University of Melbourne, Australia), Daniel Jones (New Mexico Institute of Mining and Technology, USA), Andrea García Bravo (Institut de Ciències del Mar, Institute of Marine Sciences, Spain), Stefan Bertilsson (SLU, Sveriges lantbruksuniversitet, Swedish University of Agricultural Sciences, Sweden), John Moreau (University of Glasgow, UK), Katherine McMahon (University of Wisconsin, USA), Dwayne Elias (Oak Ridge National Laboratory, USA), and Cynthia Gilmour (Smithsonian Environmental Research Center, USA). This work is an initiative from members of the <a href="https://ercapo.wixsite.com/meta-hg" target="_blank"><b>Meta-Hg working group</b></a>.
</p>

## How to cite us
<p align="justify">
Gionfriddo, C., Capo, E., Peterson, B., Lin, H., Jones, D., Bravo, AG., Bertilsson, S., Moreau, J., McMahon, K., Elias, D., and Gilmour, C. (2021). Hg-MATE-Db.v1.01142021. doi:10.25573/serc.13105370 
</p>

