# 1117_to_1123 Playimg Around
## Todo

This week:

> - [x] look through other's GitHub analysis for gene
> - [ ] have a draft of topics
> - [x] take at least 2 lectures of each course
>   - with an asterisk(*) It takes very long to digest and understand one lecture. I'll have to look up many terms as the explanation in the lecture was too hard.
>   - [x] 1 lecture
> - [x] at least complete GEO analysis to get an idea of these analysis
> - [x] play with TCGA
>   - [x] play with GEO
>   - [x] try the analysis tools listed in the research paper
## Definitions for Genetics 
### Functional Genomics [source](https://www.ebi.ac.uk/training/online/courses/functional-genomics-i-introduction-and-design/what-is-functional-genomics/)
>- **Functional genomics**:  focuses on the ==dynamic expression== of gene products in a specific context
>     -   DNA level (genomics and epigenomics)
>     -   RNA level (transcriptomics)
>     -   Protein level (proteomics)
>     -   Metabolite level (metabolomics)
>     ![Functional genomics is the study of how the genome, transcripts (genes), proteins and metabolites work together to to produce a particular phenotype|400](https://www.ebi.ac.uk/training/online/courses/functional-genomics-i-introduction-and-design/wp-content/uploads/sites/60/2020/05/Figure01-1024x747.png "Functional genomics is the study of how the genome, transcripts (genes), proteins and metabolites work together to to produce a particular phenotype")
>- **Phenotype**: the set of observable characteristics of an individual resulting from the interaction of its genotype with the environment.

#### Functional genomics case studies

Examples of biological questions that can be tackled using functional genomics experiments are:

-   Why do some cancer drugs only work effectively on a subset of patients with the disease?
-   Why are some cultivars of rice more resistant to drought than others?
-   What makes some individuals more susceptible to skin allergies?

[[Analysis Tools for TCGA]]
### Differential Gene Expression Analysis [source](https://www.ebi.ac.uk/training/online/courses/functional-genomics-ii-common-technologies-and-data-analysis-methods/rna-sequencing/performing-a-rna-seq-experiment/data-analysis/differential-gene-expression-analysis/)
- taking the normalised read count data and performing statistical analysis to discover quantitative changes in expression levels between experimental groups. For example, we use statistical testing to decide whether, for a given gene, an observed difference in read counts is significant, that is, whether it is greater than what would be expected just due to natural random variation.

![|400](https://www.ebi.ac.uk/training/online/courses/functional-genomics-ii-common-technologies-and-data-analysis-methods/wp-content/uploads/sites/70/2020/09/Fig11-updated-1024x887.png "RNA-seq processing pipeline used to generate gene expression data in Expression Atlas")
<figure>Figure 2. interesting data pipeline</figure>

## Tool
### Tool 1: GREIN ❌

![Figure 1|800](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41598-019-43935-8/MediaObjects/41598_2019_43935_Fig1_HTML.png)
⬆️ A schematic diagram for GREIN's workflow!

![[截圖 2021-11-16 下午10.16.33.png]]

However, the server seems to be shut down 🤧.

### Tool 2: GEO2R ✅

![[截圖 2021-11-16 下午10.46.27.png]]
I was greeted with this and it seems so interesting!

- [x] look into what those plots mean
	- It is the volcano plot! The “_Volcano Plot_” function is a common way of visualising the results of a DE analysis. The x axis shows the log-fold change and the y axis is some measure of statistical significance, which in this case is the log-odds, or “B” statistic. A characteristic “volcano” shape should be seen.
- [x] see what log2 means to the data
- [ ] find the one that's most useful


## Analysis
### [Analysing data from GEO - Work in Progress](https://sbc.shef.ac.uk/geo_tutorial/tutorial.nb.html#Introduction)
#### Print info
```r
library(GEOquery)
## change my_id to be the dataset that you want.
my_id <- "GSE33126"
gse <- getGEO(my_id)
pData(gse) ## print the sample information
fData(gse) ## print the gene annotation
exprs(gse) ## print the expression data
```
#### Inspect Clinical Variables
I will need to inspect what variables will be useful

#### Sample Clustering and Principal Component Analysis
```r
pheatmap()
```
![[Pasted image 20211121001334.png|500]]
#### Doing PCA
Useful [StatsQuest video](https://www.youtube.com/watch?v=0Jp4gsfOLMs)

Need to first transpose the data so that we see how samples are related (and NOT GENES)
![[截圖 2021-11-21 下午1.53.26.png|500]]
![[截圖 2021-11-21 下午1.55.47.png|500]]
![[截圖 2021-11-21 下午2.00.30.png|500]]

#### Differential Expression with *limma* library

I will first need to do create design matrix (設計矩陣在統計學和機器學習中，是一組觀測結果中的所有解釋變量的值構成的矩陣，常用X表示。設計矩陣常用於一些統計模型，如一般線性模型，方差分析中。). A useful function for that is 
```r
model.matrix()
```
It creates a design matrix for a column I choose

I was confused with this line
```r
design <- model.matrix(~0+sampleInfo$group)
```
I didn't understand the ```~0``` that happens before the ```sampleInfo$group```

Thus, I looked up in [StackOverflow](https://stackoverflow.com/questions/12737783/r-tilde-operator-what-does-0a-means) and found that it ensures the y-intercept is 0 -> passes the origin. 

Next, I used dataset gene expression's median as a baseline and cutoff the genes that express below median

```r
# only keeps genes that are expressed in more than 2 samples
keep <- rowSums(is_expressed) > 2
table(keep)
View(keep)
# now, we subset to only those kept genes
gse <- gse[keep, ]
```

```r
fit <- lmFit(exprs(gse), design)
head(fit$coefficients)
```

```bash
                Normal    Tumour
ILMN_1343291 16.087740 16.004200
ILMN_1343295 14.032346 14.699567
ILMN_1651199  7.786860  7.763617
ILMN_1651209  8.079803  8.002217
ILMN_1651210  7.555458  7.659205
ILMN_1651221  7.816231  7.801812
```

```r
contrast <- makeContrasts(Tumor - Normal, levels=design)
fit2 <- contrasts.fit(fit, contrast)

fit2 <- eBayes(fit2)

View(fit2)

topTable(fit2)

topTable(fit2, coef=1)

### to see the results of the second contrast (if it exists)
## topTable(fit2, coef=2)
```

#### Coping with Outliers
>It is tempting to discard any arrays which seem to be outliers prior to differential expressions. However, this is done at the expense of sample-size which could be an issue for small experiments. A compromise, which has been ==shown to work well is to calculate _weights_ to define the reliability of each sample.==

The `arrayWeights` function will assign a score to each sample; with a value of 1 implying equal weight. Samples with score less than 1 are down-weights, and samples with scores greater than 1 are up-weighted. Therefore no samples actually need to be removed.

with `arrayWeights`, we can then include it into the fitting
```
fit <- lmFit(exprs(gse), design,
             weights = aw)
contrasts <- makeContrasts(Tumour - Normal, levels=design)
fit2 <- contrasts.fit(fit, contrasts)
fit2 <- eBayes(fit2)
```

#### Further processing and visualisation of DE results


![[Pasted image 20211121164418.png|500]]

![[Pasted image 20211121165500.png|500]]

#### Get results from a particular gene

### Using Galaxy to do the same analysis!
Duration: 1 minutes 😨

![[截圖 2021-11-21 下午6.16.10.png|400]]

Duration: 20 seconds 😨

![[截圖 2021-11-21 下午6.25.04.png|400]]
![[截圖 2021-11-21 下午6.30.45.png|400]]

## Paper and methods
### [Integrative Bioinformatics and Functional Analyses of GEO, ENCODE, and TCGA Reveal FADD as a Direct Target of the Tumor Suppressor BRCA1](https://www.mdpi.com/1422-0067/19/5/1458/htm)
1. Tumor Suppressor [BRCA1](https://www.ntuh.gov.tw/gene-lab-mollab/Fpage.action?muid=4048&fid=3866)
2. **Identification of Potential BRCA1 Target Genes from ENCODE, GEO, and TCGA Data Analysis**

### Survival Analysis of Cancer Patients with the TCGA Datasets
1. [Journals](https://www.google.com/search?q=survival+analysis+journal+tcga&client=firefox-b-d&biw=1280&bih=687&ei=vmKaYYG4Eabm2roPq4y9sA4&ved=0ahUKEwiBj9Dp36n0AhUms1YBHStGD-YQ4dUDCA0&uact=5&oq=survival+analysis+journal+tcga&gs_lcp=Cgdnd3Mtd2l6EAM6BwgAELADEBM6CwgAELADEAgQHhATOgQIABATOgYIABAeEBM6BQghEKABSgQIQRgBUNUBWMcfYIEhaAJwAHgAgAHZAYgBkgmSAQU0LjQuMZgBAKABAcgBA8ABAQ&sclient=gws-wiz)

### [Statistically identifying tumor suppressors and oncogenes from pan-cancer genome-sequencing data](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4757952/)

The ones from Emerging Scholars
![[21-050R3 Selver proof_final.pdf]]
![[21-099_final.pdf]]
![[JEI-20-029-fi![[2018.1_analysis_of_second_primary_cancers_final.pdf]]nal.pdf]]

## Next Week
Goal for next two week: [[1124_to_1130 SetTopics#Todo]]
- [x] look into the journals listed above

- [x] draft potential research topics for each of them

- [x] **REMEBER!** to evaluate each of them's practicality







#bioinformatics #research #project #fun