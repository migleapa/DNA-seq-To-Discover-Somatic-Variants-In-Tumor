# DNA-seq-To-Discover-Somatic-Variants-In-Tumor

2 sets of paired-end seq FASTQ (gzip compressed) files were used: 
       1) Tumour: tumour_R1.fq.gz and tumour_R2.fq.gz. 
       2) Matched normal control: germline_R1.fq.gz and germline_R2.fq.gz
       
 Pipeline:
 
 1) Aligning the FASTQ files to chromosome 17 using BOWTIE2, using the existing BOWTIE2 chromosome 17 reference index files.
 2) Marking duplicate reads in the 4 alignment files.
 3) Running Base Score Quality Recalibration (following the GATK workflow)
      * Reporting all the command lines for the analysis above and “samtools flagstat” output of the final processed BAM files of tumour and germline control
 4) Runing VarScan on tumour sample only against the reference genome (chromosome 17) to identify all the variants and generating the VCF variant file.
 5) Using Annovar to filter the list of variants against 1000G and exome sequencing project, removing all variants that occur in more than 1% of the cases in these datasets. Then using Annovar to annotate the remaining variants with gene names, dbSNP id and cosmic id.
6) Filtering out variants with a variant allele frequency of <10%.
      * Reporting all the command lines and analytic steps for the analysis above.
7) Obtaining variants for gene TP53 And listing the coordinate of the variants in chromosome 17; the mutation, e.g., reference allele, mutated allele; the annotation of this variant(s), such as cDNA position, affected amino acid, the change of the amino acid.
8) Using VarScan in the somatic mode to run the tumour and germline samples together (using germline as control), generating the resulting VCF file of all somatic mutations, and annotating mutations using ANNOVAR. 
     *  Reporting all the command lines and analytic steps for the analysis above.
9) Listing mutations in the mutation(s) in gene TP53, with all associated annotation and the variant allele frequency of the mutation(s) in TP53
