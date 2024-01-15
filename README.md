## An Error Taxonomy for Advancing Systematic Error Analysis in Multi-site Electronic Health Record-based Clinical Concept Extraction

Welcome to our Error Taxonomy project! We have iteratively developed and evaluated an error taxonomy based on existing literature, standards, real-world data, multisite case evaluations, and community feedback.

The finalized taxonomy is available in both .dtd and .owl formats at the OHNLP consortium. It is also compatible with several different open-source annotation tools, including MAE, Brat, and MedTator.

### Project Development Overview
![Development](https://github.com/OHNLP/ErrorAnalysis/blob/main/images/development.png)

### MedTator Error Annotation Module
Here's an example of our error annotation analytical module in MedTator. This module provides various features:

- **Error Summary Tab:** Post-error summary statistics.
- **Error Distribution:** Visualizes the distribution of errors.
- **Tag Distribution:** t-SNE visualization of error textual cosine similarity.
- **Error List:** Displays a list of errors.

This visual analytics module helps break down the number of false positive and negative cases, followed by error dimensions (annotation, contextual, linguistic, and logic), and each unique error type and specific concept.

![MedTator Error Module](https://github.com/OHNLP/ErrorAnalysis/blob/main/images/fig_erra.jpg)
