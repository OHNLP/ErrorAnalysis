## A Taxonomy for Advancing Systematic Error Analysis in Multi-site Electronic Health Record-based Clinical Concept Extraction

Welcome to our Error Taxonomy project! The finalized taxonomy is available in both .dtd and .owl formats. It is also compatible with several different open-source annotation tools, including MAE, Brat, and MedTator. 

Full Taxonomy: [https://github.com/OHNLP/ErrorAnalysis/tree/main/Taxonomy](https://github.com/OHNLP/ErrorAnalysis/blob/main/Taxonomy/error_taxonomy.md)

Online demo: https://medtator.ohnlp.org/.

Select: Sample > Error Analysis of NLP System Results > Parse

### Project Development Overview
We have iteratively developed and evaluated an error taxonomy based on existing literature, standards, real-world data, multisite case evaluations, and community feedback.
![Development](https://github.com/OHNLP/ErrorAnalysis/blob/main/images/development.png)

### MedTator Error Annotation Module
Here's an example of our error annotation analytical module in MedTator. This module provides various features:

- **Error Summary Tab:** Post-error summary statistics.
- **Error Distribution:** Visualizes the distribution of errors.
- **Tag Distribution:** t-SNE visualization of error textual cosine similarity.
- **Error List:** Displays a list of errors.

This visual analytics module helps break down the number of false positive and negative cases, followed by error dimensions (annotation, contextual, linguistic, and logic), and each unique error type and specific concept.

![MedTator Error Module](https://github.com/OHNLP/ErrorAnalysis/blob/main/images/fig_erra.jpg)

### Collaboration Sites
Mayo Clinic, Rochester, Minnesota 
University of Texas Health Science Center at Houston, Houston, Texas
University of Massachusetts Chan Medical School, Boston, Massachusetts
University of Pittsburgh, Pittsburgh, Pennsylvania
University of Minnesota, Minneapolis, Minnesota
Yale University, New Haven, Connecticut

### Reference
Sunyang Fu, Liwei Wang, Huan He, Andrew Wen, Nansu Zong, Anamika Kumari, Feifan Liu, Sicheng Zhou, Rui Zhang, Chenyu Li, Yanshan Wang, Jennifer St Sauver, Hongfang Liu, Sunghwan Sohn, A taxonomy for advancing systematic error analysis in multi-site electronic health record-based clinical concept extraction, Journal of the American Medical Informatics Association, 2024;, ocae101, https://doi.org/10.1093/jamia/ocae101

Liu H, Fu S, Lu Q, Ahn J, Chen F, Yin H, Wen J, Yue Z, Harrison T, Jun J, Ruan X. MedError: A Machine-Assisted Framework for Systematic Error Analysis in Clinical Concept Extraction. Research Square. 2025 Sep 17:rs-3.


