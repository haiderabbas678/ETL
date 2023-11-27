# ETL

Description:
This script is written in the r programming language and it performs the task of extracting, transforming and loading the -CCLE_RNAseq_rsem_genes_tpm_20180929.txt.gz and Cell_lines_annotations_20181226.txt as follows:

Extract:
● Use the DepMap Portal API to fetch cancer cell line datafiles -
CCLE_RNAseq_rsem_genes_tpm_20180929.txt.gz and
Cell_lines_annotations_20181226.txt
(Files were manually downloaded and converted to CSV files. However, this process can also be done by setting a conda environment to interact with the Dep Map API (conda install -c bioconda bioconductor-depmap) to extract the files)

Transform:
● Load both files with variable names:
rnaseq_tpm → CCLE_RNAseq_rsem_genes_tpm_20180929.txt.gz and
rnaseq_metadata → Cell_lines_annotations_20181226.txt
● Check for column wise missing values in rnaseq_metadata and drop the columns with more than 700 missing values (NA and/or blank spaces)
● Load rnaseq_tpm
   ○ Drop column named transcript_ids
  ○ Create a new dataframe by applying the following transformation on the numeric values-Log2(x+0.001) where x = numeric
● Subset rnaseq_metadata based on common cell line names between rnaseq_metadata and rnaseq_tpm (Hint: Use column CCLE_ID. You should get 1019 cell lines in common)
● Check if the order of cell line column names starting from column B (ie, 22RV1_PROSTATE) is the same as the column CCLE_ID in rnaseq_metadata. If not, please reorder rnaseq_metadata dataframe based on rnaseq_tpm cell line names

Load:
● Save the transformed data into CSV files.

Dependencies
- dyplr package in R (Other built-in packages don't need to be called from a library)
  
