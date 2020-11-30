# HDS Package

Age-dependent dysregulation of transcription regulatory machinery triggers modulations in the gene expression levels leading to the decline in cellular fitness. Tracking of these transcripts along the temporal axis in multiple species revealed a spectrum of evolutionarily conserved pathways, such as electron transport chain, translation regulation, DNA repair, etc. Recent shreds of evidence suggest that aging deteriorates the transcription machinery itself, indicating the hidden complexity of the aging transcriptomes. This reinforces the need for devising novel computational methods to view aging through the lens of transcriptomics. Here, we present Homeostatic Divergence Score (HDS) to quantify the extent of messenger RNA (mRNA) homeostasis by assessing the balance between spliced and unspliced mRNA repertoire in single cells. By tracking HDS across single-cell expression profiles of human pancreas we identified a core set of 171 transcripts undergoing an age-dependent homeostatic breakdown. Notably, many of these transcripts are well-studied in the context of organismal aging. Our preliminary analyses in this direction suggest that mRNA processing level information offered by single-cell RNA sequencing (scRNA-seq) data is a superior determinant of chronological age as compared to transcriptional noise.

# Instructions

## How to install?
1. These are are required packages: 
	time, scipy, pickle, numpy, pandas, velocyto, scanpy, anndata, matplotlib, seaborn matplotlib_venn, 		matplotlib.gridspec and scikit-learn
2. To install these packages use below command
	!pip install time scipy pickle numpy pandas velocyto scanpy anndata matplotlib seaborn matplotlib_venn 		matplotlib.gridspec scikit-learn
3. Get latest version of HDS from the link given below:
	https://test.pypi.org/project/HDS-krishang
4. Install it using below command.
	pip install -i https://test.pypi.org/simple/ HDS-krishang

## How to use?
1. from HDS import HDS
   HDS("path of loom file") 
   For example: HDS("/home/krishan/loom/abc.loom")
2. Use cluster parameter to pass cell's clusters if you have. By default  HDS uses 'leiden' method with resolution = 	1 inbuilt in scanpy package. Note: clusters labels should be in same order as in barcode in loom file.
   For example:
   HDS(path1="path of loom file", cluster=[1,2,1,2,3,4,5])
3. Use genes parameter to pass speific genes.
   For example:
   HDS(path1="path of loom file", genes=['Fos','Fosl1'])
4. For other parameters default values are:
   min_genes=200, min_cells=3, n_genes_by_counts=2500, pct_counts_mt=5
   
## Expected outcome?
### Rsquare and mutual information score
![Rsquare and mutual information score](https://github.com/krishan57gupta/HDS/blob/main/images/violin_plot.png?raw=true)
### portrait of rhomeostatis genes
![portrait of rhomeostatis genes](https://github.com/krishan57gupta/HDS/blob/main/images/HDS.png?raw=true)



