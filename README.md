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
* [An endometrioid cancer case](https://www.cbioportal.org/patient?studyId=ucec_tcga&caseId=TCGA-BK-A0CC)
	* Mutations and copy-number events are sorted based on recurrence and prior knowledge
	* PPP2R1A mutation: Gene is significantly mutated according to **MutSig**, 17 occurrences in **COSMIC**, likely oncogenic according to **OncoKB**, **3D Hotspot** with 3-D structure available
	* **Tissue Images** Tab gives you access to the original histology images
	* The detailed pathology report can be viewed on the **Pathology Report** Tab

### Example 8: Study view

Choose the study and click the **pie plot** icon.

* [TCGA endometrial cancer study](http://www.cbioportal.org/study?id=ucec_tcga_pub)
	* Select the copy-number high subtype in the **Subtype** pie chart
	* In the **Chart** Tab in the upper right, click **Reset chart**, then choose **Tumor Stage 2009**. In the upper right of button **Tumor Stage 2009** pie chart, choose **Compare Groups**
	* Select the tumors with more than 5000 mutations in the **Mutation Count vs CNA** scatter plot by dragging a rectangle using mouse
	* Query the top 3 mutated genes

### Example 9: Group comparison between primary and metastasis tumor

* Comparison of primary vs metastatic prostate cancer
	* Open [MSK-IMPACT clinical sequencing cohort](https://www.cbioportal.org/study/summary?id=msk_impact_2017)
	* Select **Prostate Cancer** in Cancer Type table
	* In **Sample Type** chart, click **menu** -> **Compare Groups**

### Example 10: Cross-study queries

* [ERBB2 mutations across all TCGA provisional studies](https://www.cbioportal.org/results/cancerTypesSummary?Action=Submit&Z_SCORE_THRESHOLD=2.0&tab_index=tab_visualize&data_priority=0&case_set_id=all&gene_list=ERBB2&RPPA_SCORE_THRESHOLD=2.0&cancer_study_list=laml_tcga%2Cacc_tcga%2Cblca_tcga%2Clgg_tcga%2Cbrca_tcga%2Ccesc_tcga%2Cchol_tcga%2Ccoadread_tcga%2Cesca_tcga%2Cgbm_tcga%2Chnsc_tcga%2Ckich_tcga%2Ckirc_tcga%2Ckirp_tcga%2Clihc_tcga%2Cluad_tcga%2Clusc_tcga%2Cdlbc_tcga%2Cmeso_tcga%2Cov_tcga%2Cpaad_tcga%2Cpcpg_tcga%2Cprad_tcga%2Csarc_tcga%2Cskcm_tcga%2Cstad_tcga%2Ctgct_tcga%2Cthym_tcga%2Cthca_tcga%2Cucs_tcga%2Cucec_tcga%2Cuvm_tcga)
	* Explore **OncoPrint** Tab
	* Explore **Cancer Types Summary** Tab
	* **Expression** Tab
	* **Mutations** Tab
* [BRAF V600E mutations across all cancer types (BRAF: MUT = V600E)](http://www.cbioportal.org/index.do?session_id=5a0b48e6498e5df2e29836f0&show_samples=false&clinicallist=CANCER_STUDY&)

### Example 11: Merging studies into a virtual study

* Select MSK-IMPACT Clinical Sequencing Cohort (MSKCC, Nat Med 2017)
* Select All Breast studies (for Breast TCGA, select Cell 2015 only)
* Click **View summary** to open Study View
* Select **Breast Cancer** from Cancer Type table
* Click on the Bookmark icon to create a virtual study

### Example 12: Overview of the MSK-IMPACT cohort via the study view

* Select MSK-IMPACT **study view**
* Explore the most frequently mutated and copy-number altered genes across all samples. What are the top 3 mutated, amplified, and deleted genes?
* What is the balance of primary and metastatic tumors? Male vs female?
* What is the sample with the highest number of mutations? (Hint: drag points in **Mutation Count vs Fraction of Genome Altered**)
* Which patient has the largest number of sequenced samples?
* How many patients are Part C consented? (Hint: Use the "Add Chart" menu in the top right corner.)
* What are the most frequently altered genes in metastatic breast cancer?

### Example 13: cBioPortal patient view

* What is the likely cause of hypermutation in the sample with the largest number of mutations? (Hint: **Clinical Data** tab)
* What is the likely cause of hypermutation in the second sample of this glioma patient?

### Example 14: ESR1 mutations

* Run a query for ESR1 mutations across the entire MSK-IMPACT cohort. (Hint: Select MSK-IMPACT and type *ESR1: MUT FUSION* in **Query By Gene**)
* What is the tumor type with the highest mutation frequency? Use the **Cancer Types Summary** tab, limit to cancer types with 50 or more tumors (via the customize button)
* How do mutations in breast and endometrial cancer differ from those in lung cancer? Are the differences related to overall mutation numbers in the samples? (Hint: Use the **Mutations** tab and filter via the search box in the table.)
* Do mutation rates in samples with known ESR1 driver mutations differ from those with unknown mutations? Add **Mutation count** as a clinical track in the **OncoPrint**.
* Assess the distribution of mutations between primary and metastatic samples in the OncoPrint. Add **Cancer Type** and **Sample Type** as clinical tracks.

### Example 15: Mutual exclusivity of alterations in non-small cell lung cancer (NSCLC)

* Run a query for the known mitogenic drivers (**EGFR ALK ROS1 RET ERBB2 MET FGFR1 KRAS HRAS NRAS NF1 BRAF MAP2K1**) in NSCLC and explore the OncoPrint.
* Add **Mutation count** and **Mutation spectrum** as clinical tracks.
* Explore known or likely driver mutations vs putative passenger mutations. Is there a correlation with mutation burden?
* Is there a difference in mutation spectrum between EGFR missense mutations and in-frame insertions / deletions?
* Hide the putative passenger mutations via the **Mutation** Tab -> **Color** menu. Does the mutual exclusivity between alterations increase?