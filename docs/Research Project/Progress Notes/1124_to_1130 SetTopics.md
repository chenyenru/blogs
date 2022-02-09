## Todo

This week:
>- [x] look into the journals listed above
>- [x] draft potential research topics for each of them
>- [x] **REMEBER!** to evaluate each of them's practicality

## Paper and methods (**from last time**)

### [Integrative Bioinformatics and Functional Analyses of GEO, ENCODE, and TCGA Reveal FADD as a Direct Target of the Tumor Suppressor BRCA1](https://www.mdpi.com/1422-0067/19/5/1458/htm)

1.  Tumor Suppressor [BRCA1](https://www.ntuh.gov.tw/gene-lab-mollab/Fpage.action?muid=4048&fid=3866)
2.  **Identification of Potential BRCA1 Target Genes from ENCODE, GEO, and TCGA Data Analysis**

### Survival Analysis of Cancer Patients with the TCGA Datasets

1.  [Journals](https://www.google.com/search?q=survival+analysis+journal+tcga&client=firefox-b-d&biw=1280&bih=687&ei=vmKaYYG4Eabm2roPq4y9sA4&ved=0ahUKEwiBj9Dp36n0AhUms1YBHStGD-YQ4dUDCA0&uact=5&oq=survival+analysis+journal+tcga&gs_lcp=Cgdnd3Mtd2l6EAM6BwgAELADEBM6CwgAELADEAgQHhATOgQIABATOgYIABAeEBM6BQghEKABSgQIQRgBUNUBWMcfYIEhaAJwAHgAgAHZAYgBkgmSAQU0LjQuMZgBAKABAcgBA8ABAQ&sclient=gws-wiz)

### [Statistically identifying tumor suppressors and oncogenes from pan-cancer genome-sequencing data](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4757952/)


### [Bioinformatics prediction of differential miRNAs in non-small cell lung cancer](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0254854)
**aim**: screen miRNAs associated with 非小細胞肺癌(_NSCLC_) ... 非小細胞肺癌是最常見的肺癌種類 85% of all lung cancer
**method**: 
	- **dataset**: tcga and geo dataset. --> wow! this is exactly what i could do
	- **analysis**: ROC analysis, survival analysis, and enrichment analysis (GO term and KEGG pathway).
	
21 meaningful differentially expressed miRNAs were identified from NSCLC tissues and adjacent tissues. 
- **ROC Analysis**: The receiver operating characteristic (ROC) curve was used to analyze the sensitivity and specificity of the 4 miRNAs with the most differences, including hsa-mir-30a, hsa-mir-338, hsa-mir-451a, and hsa-mir-4732. 
- **Survival Analysis**: In addition, we also performed survival analysis, gene ontology (GO) terminology, and KEGG function prediction analysis on hsa-mir-30a, which is the most differentially expressed, to determine the related expression functions and pathways of hsa-mir-30a. Differentially expressed miRNAs were identified from NSCLC tissues and paracancerous tissues. And we hope to provide a potential development direction for the treatment of NSCLC.

In this study, we obtained all miRNAs in NSCLC tissues and paracancerous tissues from the TCGA database and GEO database. 21 meaningful differentially expressed miRNAs were identified from NSCLC tissues and adjacent tissues. The receiver operating characteristic (ROC) curve was used to analyze the sensitivity and specificity of the 4 miRNAs with the most differences, including ==hsa-mir-30a, hsa-mir-338, hsa-mir-451a, and hsa-mir-4732==. In addition, we also performed *survival analysis*, gene ontology *(GO) terminology*, and *KEGG function prediction analysis* on hsa-mir-30a, which is the most differentially expressed, to determine the related expression functions and pathways of hsa-mir-30a. Differentially expressed miRNAs were identified from NSCLC tissues and paracancerous tissues. And we hope to provide a potential development direction for the treatment of NSCLC.


#### 2.1. Data selection

We screened 52 NSCLC tissue specimens and 8 normal specimens from the TCGA database ([https://portal.gdc.cancer.gov/](https://portal.gdc.cancer.gov/)). The RNA-seq data of these samples were downloaded and analyzed. Furthermore, the raw sequencing data of 5 NSCLC tissue samples and 5 normal samples were downloaded from the National Center for Biotechnology Information (NCBI) GEO database ([http://www.ncbi.nlm.nih.gov/geo/](http://www.ncbi.nlm.nih.gov/geo/)) (GSE135918).

--> Hmm, maybe I can use a similar approach 🤓

#### 2.2. MiRNA screening and visualization
- Bioconductor DESeq2 package
- volcano maps (hehe used it last time)
#### 2.3. ROC diagnosis and survival curve
#### 2.4. GO and KEGG pathway enrichment analysis

### [Bioinformatics Analysis of ZBTB16 as a Prognostic Marker for Ewing’s Sarcoma](https://www.hindawi.com/journals/bmri/2021/1989917/)
- _Objective_. The purpose of this study is to identify novel biomarkers for the prognosis of **Ewing’s sarcoma** based on bioinformatics analysis.
- _Methods_. The ==GSE63157 and GSE17679 datasets== contain patient and healthy control microarray data that were downloaded from the Gene Expression Omnibus (**GEO**) database and analyzed through R language software to obtain differentially expressed genes (**DEGs**). Firstly, Gene Ontology (**GO**) and Kyoto Encyclopedia of Genes and Genomes (**KEGG**) functional enrichment, protein-protein interaction (**PPI**) networks, and Cytoscape Molecular Complex Detection (**MCODE**) plug-in were then used to compute the highest scores of the module. After survival analysis, the hub genes were lastly obtained from the two module genes. 
- _Results_. A total of 1181 DEGs were identified from the two GSEs. Through MCODE and survival analysis, we obtain 53 DEGs from the module and 29 overall survival- (OS-) related genes. *ZBTB16 was the only downregulated gene after Venn diagrams (hmm, seems plausible)* . **Survival analysis** indicates that there was a significant correlation between the high expression of ZBTB16 and the OS of Ewing’s sarcoma (ES), and the low expression group had an unfavorable OS when compared to the high expression group.
- _Conclusions_. High expression of ZBTB16 may serve as a predictor biomarker of poor prognosis in ES patients.
### [Bioinformatics Analysis of Differentially Expressed Genes and miRNAs in Low-Grade Gliomas](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7649870/)

### [Identification of miR-18a-5p as an oncogene and prognostic biomarker in RCC](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6038077/)

### [Comprehensive bioinformatics analysis of the TP53 signaling pathway in Wilms’ tumor](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7607069/)

- 
- prognostic role of TP53 in WT were investigated using [cBioPortal](https://www.cbioportal.org/)
- 



## Potential Topics
1. [PRCC](https://portal.gdc.cancer.gov/genes/ENSG00000143294) papillary renal cell carcinoma (translocation-associated)
	- Bioinformatics prediction of differential miRNAs in papillary renal cell carcinoma
	- Bioinformatics prediction of differential miRNAs in sarcoma
	- Bioinformatics Analysis of (_Gene Name_) as a Prognostic Marker for 
2. Clarify _a gene_ as a prognostic marker


download data and see see

- choose method
- find other datasets

[[blogs/docs/Research Project/Progress Notes/1201_to_1208 Reading Papers for Topics]]
