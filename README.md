# HDS Package

Age-dependent dysregulation of transcription regulatory machinery triggers modulations in the gene expression levels leading to the decline in cellular fitness. Tracking of these transcripts along the temporal axis in multiple species revealed a spectrum of evolutionarily conserved pathways, such as electron transport chain, translation regulation, DNA repair, etc. Recent shreds of evidence suggest that aging deteriorates the transcription machinery itself, indicating the hidden complexity of the aging transcriptomes. This reinforces the need for devising novel computational methods to view aging through the lens of transcriptomics. Here, we present Homeostatic Divergence Score (HDS) to quantify the extent of messenger RNA (mRNA) homeostasis by assessing the balance between spliced and unspliced mRNA repertoire in single cells. By tracking HDS across single-cell expression profiles of human pancreas we identified a core set of 171 transcripts undergoing an age-dependent homeostatic breakdown. Notably, many of these transcripts are well-studied in the context of organismal aging. Our preliminary analyses in this direction suggest that mRNA processing level information offered by single-cell RNA sequencing (scRNA-seq) data is a superior determinant of chronological age as compared to transcriptional noise.

# Instructions

## How to install?
1. These are are required packages: 
   scipy, numpy, pandas, velocyto, scanpy, anndata, matplotlib, seaborn matplotlib_venn, leidenalg and scikit-learn

2. To install these packages use below command
   !pip install scipy numpy pandas velocyto scanpy anndata matplotlib seaborn matplotlib_venn leidenalg scikit-learn

3. Get latest version of HDS from the link given below:
   https://test.pypi.org/project/HDS-krishang

4. Install it using below command.
   pip install -i https://test.pypi.org/simple/ HDS-krishang

## How to make loom files from fastq files?
1. Download fastq files from the link given below:
   https://www.ebi.ac.uk/arrayexpress/experiments/E-MTAB-6687/samples/
   
2. For 10x fastq files, use the 'cellranger count' command to generate bam file.
   For example: 
   cellranger count --id=$sample --transcriptome=$transcriptome --fastqs=/sample.fastqs --sample=$sample --expect-cells=8000 --localcores=12
   Download transcriptome from https://support.10xgenomics.com/single-cell-gene-expression/software/downloads/latest

3. 'STAR' tool can also be used for alignment to reference genome and generate bam file.
   For example:
   STAR --runThreadN 12 --genomeDir /star_mouse/index --sjdbGTFfile /gencode.vM25.primary_assembly.annotation.gtf --readFilesIn $line1.fastq.gz $line2.fastq.gz --outFileNamePrefix $line.bam --readFilesCommand zcat --outSAMtype BAM SortedByCoordinate
   1. Create star index using standard parameters
   2. Download gtf file from the link https://www.gencodegenes.org/human

4. Generate the loom file using velocyto command.
   For example:
   For 10x data, use the command written below:
   velocyto run10x -m hg19_rmsk.gtf sample_folder/01 refdata-gex-GRCh38-2020-A/genes/genes.gtf
   1. Download gtf file from link: https://www.gencodegenes.org/human/
   2. Download mask file from link: https://genome.ucsc.edu/cgi-bin/hgTables?hgsid=611454127_NtvlaW6xBSIRYJEBI0iRDEWisITa&clade=mammal&org=Human&db=0&hgta_group=allTracks&hgta_track=rmsk&hgta_table=rmsk&hgta_regionType=genome&position=&hgta_outputType=gff&hgta_outFileName=mm10_rmsk.gtf
   3. For STAR generated bam files, use the command written below:
    velocyto run -b filtered_barcodes.tsv -o output_path -m repeat_msk_srt.gtf possorted_genome_bam.bam mm10_annotation.gtf

## How to use?
1. from HDS import HDS
   HDS("path of loom file") 
   For example: HDS("/home/krishan/loom/abc.loom")
2. Use 'clusters' parameter to pass cell's clusters if you have. By default  HDS uses 'leiden' method with
   resolution = 1, inbuilt in scanpy package. Note: clusters labels should be in the same order as barcode in the
   loom file.
   For example:
   HDS(path1="path of loom file", clusters=[1,2,1,2,3,4,5])
3. Use 'genes' parameter to pass speific genes.
   For example:
   HDS(path1="path of loom file", genes=['Fos','Fosl1'])
4. For other parameters default values are:
   min_genes=200, min_cells=3, n_genes_by_counts=2500, pct_counts_mt=5
5. We have created a [google colab](https://colab.research.google.com/drive/138HaACR90z_ELCPAm2DbTPHccH0G26Ov?usp=sharing) with the code and loom file. Link is given below:
   https://drive.google.com/drive/folders/1Pq9IsjnCYaJngU8WQ0E1RjIqA9f-j3lY?usp=sharing
   
## Output?
### Clusters with Rsquared and Mutual Information scores
![Rsquare and mutual information score](https://github.com/krishan57gupta/HDS/blob/main/images/violin_plot.png?raw=true)
### Phase portrait of genes under ageing homoestasis break down
![portrait of rhomeostatis genes](https://github.com/krishan57gupta/HDS/blob/main/images/HDS.png?raw=true)
