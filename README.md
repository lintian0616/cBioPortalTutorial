# cBioPortalTutorial
Note from MSKCC [cBioPortal](https://www.cbioportal.org/) Workshop

General questions: [cbioportal@googlegroups.com](cbioportal@googlegroups.com)

Questions specific to MSK datasets: [cbioportal@cbio.mskcc.org](cbioportal@cbio.mskcc.org)

### Example 1: Basic query in GBM

* [Query for alterations in RB pathway genes (CDKN2A, CDK4, RB1) in Glioblastoma (TCGA, Nature 2008)](http://www.cbioportal.org/index.do?genetic_profile_ids_PROFILE_COPY_NUMBER_ALTERATION=gbm_tcga_pub_cna_consensus&Action=Submit&genetic_profile_ids_PROFILE_MUTATION_EXTENDED=gbm_tcga_pub_mutations&data_priority=0&case_set_id=gbm_tcga_pub_cnaseq&Z_SCORE_THRESHOLD=2.0&cancer_study_id=gbm_tcga_pub&gene_list=CDKN2A+CDK4+RB1&tab_index=tab_visualize&gene_set_choice=user-defined-list&)
	* Select study Glioblastoma (TCGA, Nature 2008)
	* Click on query by gene
	* Input genes: CDKN2A CDK4 RB1 and Click Submit
	* Explore mutual exclusivity via the **OncoPrint** (on **Summary** Tab) and via the **Mutual Exclusivity** Tab
	* Modify the query and add the mRNA expression profile. Compare the DNA copy-number and mRNA expression relationship for CDKN2A and CDK4.
	* Explore the relationship between DNA copy-number and mRNA expression via the **Plots** Tab. Is CDK4 up-regulated when amplified?
	* Explore how focal the CDK4 amplifications are using the **CN Segments** tab.
	* Explore mutations via the **Mutations** Tab. Are the CDKN2A and RB1 mutations known inactivating mutations?
	* Do patients with RB pathway alterations have different survival (**Survival** Tab)?

### Example 2: Onco Query Language for more detailed queries

* [Refined query for RB pathway genes (CDKN2A, CDK4, CCNE1, RB1) in Ovarian Cancer](http://www.cbioportal.org/index.do?cancer_study_list=ov_tcga_pub&cancer_study_id=ov_tcga_pub&genetic_profile_ids_PROFILE_MUTATION_EXTENDED=ov_tcga_pub_mutations&genetic_profile_ids_PROFILE_COPY_NUMBER_ALTERATION=ov_tcga_pub_gistic&Z_SCORE_THRESHOLD=2.0&data_priority=0&case_set_id=ov_tcga_pub_3way_complete&case_ids=&gene_set_choice=user-defined-list&gene_list=CDKN2A%3A+HOMDEL+MUT%0D%0ACDK4%3A+AMP%0D%0ACCNE1%3A+AMP%0D%0ARB1%3A+HOMDEL+MUT&clinical_param_selection=null&tab_index=tab_visualize&Action=Submit)

The Onco Query Language (**OQL**) is used to define which specific types of alterations are included in a query on the cBioPortal for Cancer Genomics.

OQL-specified alterations will be reflected on most tabs, including **OncoPrint**, but are **not** currently reflected on the **Plots**, **Co-Expression** or **Expression** tabs. Here is the [tutorial](https://www.cbioportal.org/oql).

Usage:

```
GENE1: OQL KEYWORDS;
GENE2: OQL KEYWORDS
```

The `QQL KEYWORDS` syntax is:

```
OQL Keywords_OQL modifiers
```

Here is an example:

```
BRAF: MUT = V600E
TP53: MUT = TRUNC INFRAME
EGFR: AMP_DRIVER MUT = MISSENSE_DRIVER
BRCA1: MUT = MISSENSE_SOMATIC_DRIVER
```

### Example 3: Variant interpretation via prior knowledge and recurrence

* [Query for EGFR in MSK IMPACT non-small cell lung cancer case list](http://www.cbioportal.org/index.do?session_id=59d5756d498e5df2e29633a4&show_samples=false&)
	* Which EGFR mutations from that query are likely drivers?
	* Use the **OncoPrint** and the **Mutations** tab and inspect annotation from OncoKB, Civic, and [CancerHotspots](cancerhotspots.org)
	* Query for driver events only by [using DRIVER in OQL](https://www.cbioportal.org/results/oncoprint?Action=Submit&RPPA_SCORE_THRESHOLD=2&Z_SCORE_THRESHOLD=2&cancer_study_list=msk_impact_2017&case_set_id=msk_impact_2017_Non-Small_Cell_Lung_Cancer&data_priority=0&gene_list=EGFR%253A%2520DRIVER&geneset_list=%20&genetic_profile_ids_PROFILE_COPY_NUMBER_ALTERATION=msk_impact_2017_cna&genetic_profile_ids_PROFILE_MUTATION_EXTENDED=msk_impact_2017_mutations&tab_index=tab_visualize&show_samples=false&clinicallist=NUM_SAMPLES_PER_PATIENT)

### Example 4: Correlation analysis between mRNA, copy number, and mutations

* [Query EGFR and TP53 in Ovarian Cancer](https://www.cbioportal.org/results/plots?session_id=5c9b9ffbe4b046111fee2f7a)
	* Analyze the correlation between copy number and gene expression for EGFR (**Plots** Tab)
	* Analyze the correlation between copy number and gene expression for TP53, and the impact of truncating mutations on expression (**Plots** Tab)

### Example 5: DNA methylation

* [Query for BRCA1/2 alterations in Ovarian Cancer](http://www.cbioportal.org/index.do?genetic_profile_ids_PROFILE_COPY_NUMBER_ALTERATION=ov_tcga_pub_gistic&Action=Submit&genetic_profile_ids_PROFILE_MUTATION_EXTENDED=ov_tcga_pub_mutations&data_priority=0&case_set_id=ov_tcga_pub_3way_complete&Z_SCORE_THRESHOLD=2.0&cancer_study_id=ov_tcga_pub&gene_list=BRCA1+BRCA2&tab_index=tab_visualize&gene_set_choice=user-defined-list&)
	* Analyze the correlation between methylation and gene expression in Plots tab. What do you see?

### Example 6: RPPA data

* [Effect of PTEN alteration (PTEN: MUT HOMDEL) on pAKT in Lung Squamous Cell Carcinoma](http://www.cbioportal.org/index.do?session_id=5a0b42fa498e5df2e29836a1&show_samples=false&)
	* use the **Enrichments** Tab, then select **Protein**

### Example 7: cBioPortal Patient View

* [Query KRAS NRAS in Endometrial TCGA](http://www.cbioportal.org/index.do?session_id=59f0fe51498e5df2e2973452&show_samples=false&) and Investigate [the case](http://www.cbioportal.org/case.do?case_id=TCGA-B5-A0JV&cancer_study_id=ucec_tcga_pub) with co-occurring oncogenic RAS mutations.
	* Explore the distribution of the variant allele frequencies of the major oncogenic mutations. Are the NRAS and KRAS mutations clonal or subclonal?
* An endometrioid cancer case


