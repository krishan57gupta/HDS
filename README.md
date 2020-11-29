# HDS Package

This is a simple package. You can use it to defines aging using decline in transcriptional homeostasis.

# First of all, you should have installed below packages.
## time, scipy, pickle, numpy, pandas, velocyto, scanpy, anndata, matplotlib, seaborn matplotlib_venn, matplotlib.gridspec, scikit-learn.
## Can be install using below command
## !pip install time scipy pickle numpy pandas velocyto scanpy anndata matplotlib seaborn matplotlib_venn matplotlib.gridspec scikit-learn
## Then install latest version of HDS from https://test.pypi.org/project/HDS-krishang
## or type pip install -i https://test.pypi.org/simple/ HDS-krishang

# Then import package
## from HDS import HDS
## HDS("path of loom file") like HDS("/home/krishan/loom/abc.loom")
## Or you can pass clusters info also if have, it should list and in order as barcodes are order in loom file.
## HDS(path1="path of loom file", cluster=[1,2,1,2,3,4,5]), length of cells/barcodes should be same as cluster length and should be in same order.
## Or you can pass genes names to plot.
## HDS(path1="path of loom file", genes=['Fos','Fosl1']).
## You can also pass another parameter but recomended to use default.

# Other Parameters.
## r_c=0, min_genes=200, min_cells=3, n_genes_by_counts=2500, pct_counts_mt=5, resolution=1
## r_c to make cutoff on r2 score to select to genes
## min_genes, min_cells, n_genes_by_counts, pct_counts_mt are cell/gene filttering parametes as per scanpy package.
## resolution for clustering as per scanpy package.

# Note if getting error in runing pip command, please use pip3.

