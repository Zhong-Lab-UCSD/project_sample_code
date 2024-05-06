# Course Project sample code: Breast cancer classifier based on SILVER-seq data

We generated SILVER-seq data of breast cancer samples in the published work: Zhou, Z., Wu, Q., Yan, Z., Zheng, H., Chen, C.J., Liu, Y., Qi, Z., Calandrelli, R., Chen, Z., Chien, S. and Su, H.I., 2019. Extracellular RNA in a single droplet of human serum reflects physiologic and disease states. Proceedings of the National Academy of Sciences, 116(38), pp.19200-19208.). The whole dataset (raw and processed data) can be found in GEO database (GSE131512: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE131512)

This repo shows an example of breast cancer recurrence classification practice we did in our original paper (Fig 5 C and D).


## Data and source code

You'll be able to find the following files:

- `data/tpm_96_nodup.tsv`, TPM values for the 96 breast cancer samples, data for the samples are organized in columns (C1 to C96)
- `data/readcounts_96_nodup.tsv`, read counts for the 96 breast cancer samples, data for the samples are organized in columns (C1 to C96)
- `data/patient_info.csv`, meta info for all samples, the column recurStatus contains recurrence status of the corresponding donor, "R" for recurrence and "N" for non-recurrence.
- `data/preselectedList`, the 750 pre-selected breast cancer biomarker genes in Ensembl gene ID
- `breastCancerClassifier.R`, an R program for constructing a classifier for breast cancer recurrence status classification and reproducing Fig 5 C and D in our original paper based on the data in the `data` folder.


## Methods
The main steps in the source code `breastCancerClassifier.R` includ: 
- Rank pre-selected 750 biomarker genes by their differential expresssion (DESeq) p-values
- Generate subsets of biomarker genes by their rank, top 30, 60, 90, ..., 720, 750
- Use SVM to construct classifier and evaluate their performance by ROC and AUC



