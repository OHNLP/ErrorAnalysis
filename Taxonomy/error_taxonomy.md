## Summary of Common Error Types for EHR-based Clinical Concept Extraction

📂 Error Dimension | 📄 Error Class | 🔸 Error Sub-Class

- 📂 **1. [Annotation Error](#annotation-error)**

  - 📄 1.1. [Missing annotation](#missing-annotation)
  - 📄 1.2. [Guideline error](#guideline-error)
  - 📄 1.3. [Misclassification](#misclassification)

- 📂 **2. [Contextual Error](#contextual-error)**

  - 📄 2.1. [Absence of context](#absence-of-context)
  - 📄 2.2. [Certainty](#certainty)
    - 🔸 2.2.1. [Differential diagnosis](#differential-diagnosis)
    - 🔸 2.2.2. [Hypothetical language](#hypothetical-language)
    - 🔸 2.2.3. [Medical Grading](#medical-grading)
    - 🔸 2.2.4. [Negation](#negation)
    - 🔸 2.2.5. [Possible and probable language](#possible-and-probable-language)
  - 📄 2.3. [Exclusion](#exclusion)
    - 🔸 2.3.1. [Medical evaluation](#medical-evaluation)
    - 🔸 2.3.2. [Medical instruction](#medical-instruction)
    - 🔸 2.3.3. [Medical risk](#medical-risk)
    - 🔸 2.3.4. [Patient education](#patient-education)
  - 📄 2.4. [Section](#section)
  - 📄 2.5. [Temporal Status](#temporal-status)
    - 🔸 2.5.1. [History](#history)
    - 🔸 2.5.2. [Present](#present)
  - 📄 2.6. [Subject](#subject)
    - 🔸 2.6.1. [Family member](#family-member)
    - 🔸 2.6.2. [Other subject](#other-subject)

- 📂 **3. [Linguistic Error](#linguistic-error)**

  - 📄 3.1. [Morphological error](#morphological-error)
  - 📄 3.2. [Orthographic error](#orthographic-error)
    - 🔸 3.2.1. [Spelling error](#spelling-error)
    - 🔸 3.2.2. [Abbreviation error](#abbreviation-error)
  - 📄 3.3. [Semantic error](#semantic-error)
    - 🔸 3.3.1. [Homonyms](#homonyms)
    - 🔸 3.3.2. [Implied inference](#implied-inference)
    - 🔸 3.3.3. [Statistical inference](#statistical-inference)
    - 🔸 3.3.4. [Synonym](#synonym)
  - 📄 3.4. [Syntactic error](#syntactic-error)
    - 🔸 3.4.1. [Sentence boundaries](#sentence-boundaries)
  - 📄 3.5. [Typographical error](#typographical-error)

- 📂 **4. [Logic Error](#logic-error)**

  - 📄 4.1. [Logic, pattern, and rule](#logic-pattern-and-rule)

- 📂 **5. [Other Error](#other-error)**
  - 📄 5.1. [Incomplete extraction](#incomplete-extraction)
  - 📄 5.2. [Dictionary error](#dictionary-error)
  - 📄 5.3. [Normalization error](#normalization-error)

## Definitions and examples

**<a id="annotation-error">📂 1. Annotation Error</a>**

_Definition:_ Human error occurred during corpus annotation, which is a process involving the manual review, judgment, marking, and labeling of linguistic and clinical concepts from unstructured text.

- 📄 **<a id="missing-annotation">1.1. Missing annotation</a>**

  _Definition:_ Annotators fail to capture concepts due to human errors.

  _Example (delirium):_

  - Confusion/Disorientation Hendrich: Yes
  - Best Verbal Response Glasgow: Confused

- 📄 **<a id="guideline-error">1.2. Guideline error</a>**

  _Definition:_ Errors occur due to conflicts between the NLP definition and the annotation guideline definition. For example, the version of the guideline does not align with the NLP version.

  _Example (delirium):_

  - Guideline definition: encephalopathy = delirium positive
  - NLP definition: encephalopathy = CAM_D

- 📄 **<a id="misclassification">1.3. Misclassification</a>**

  _Definition:_ Annotators captured incorrect concepts due to human errors.

  _Example (delirium):_

  - Screening for delirium = delirium (positive)
    -> Incorrect, screening for delirium should be marked as delirium (exclusion)

**<a id="contextual-error">📂 2. Contextual Error</a>**

_Definition:_ Information found in the context of the condition that modifies individual clinical conditions.

- 📄 **<a id="absence-of-context">2.1. Absence of context</a>**

  _Definition:_ NLP model falsely or partially captures concepts due to a lack of enough context to determine the certainty, status, and subject of the expression.

  _Example (delirium):_

  - ‘Confusion’ (occurs as a single concept without context)
    _Correction:_
  - Patient has a constant confused look displayed on his/her face.

- 📄 **<a id="certainty">2.2. Certainty</a>**

  _Definition:_ NLP model falsely captures concepts due to incorrectly judging grade (within the power or capacity of someone or something), possible, probable-related terms or expressions.

  - 🔸 **<a id="differential-diagnosis">2.2.1. Differential diagnosis</a>**

    _Definition:_ Description that documents a process where clinicians consider various possible conditions or diseases that could explain a patient's symptoms before making a final diagnosis.

    _Example (SBI):_

    - One potential differential diagnosis for silent infarction could include other causes of neurological symptoms such as migraine with aura, transient ischemic attack (TIA), or small fiber neuropathy

  - 🔸 **<a id="hypothetical-language">2.2.2. Hypothetical language</a>**

    _Definition:_ Hypothesis-related concepts or expressions.

    _Example (delirium):_

    - Patient would have delirium if the CAM screening test comes out positive

  - 🔸 **<a id="medical-grading">2.2.3. Medical Grading</a>**

    _Definition:_ A model incorrectly classifies concepts due to an erroneous assessment of grade, which pertains to the ability or capacity of someone or something.

    _Example (WMD):_

    - Moderate scattered deep and subcortical punctate white matter
    - Abnormal low- density in the right parietal periventricular white matter

  - 🔸 **<a id="negation">2.2.4. Negation</a>**

    _Definition:_ NLP model falsely captures concepts due to incorrectly judging negation-related (contradiction or denial of something) terms or expressions.

    _Example (delirium):_

    - Not able to be easily aroused
    - Patient does not have encephalopathy.
    - No history of confusion

  - 🔸 **<a id="possible-and-probable-language">2.2.5. Possible and probable language</a>**

    _Definition:_ NLP model falsely captures concepts due to incorrectly interpreting possible, probable-related terms or expressions.

    _Example (WMD):_

    - Likely/probable focus of nonspecific white matter disease
    - Possibility of demyelinating disease

- 📄 **<a id="exclusion">2.3. Exclusion</a>**

  _Definition:_ NLP model falsely captures concepts because the concepts occur in a wrong context.

  - 🔸 **<a id="medical-evaluation">2.3.1. Medical evaluation</a>**

    _Definition:_ A description of a patient presenting to a clinic for evaluation and assessment of their condition. The concepts need to be excluded because they do not reflect the patient’s disease status.

    _Example (delirium):_

    - I was called to evaluate the patient for an episode of confusion
    - Patient was screened for confusion

  - 🔸 **<a id="medical-instruction">2.3.2. Medical instruction</a>**

    _Definition:_ Communication of medical information, advice, and instructions to individuals seeking healthcare or treatment.

    _Example (delirium):_

    - When to Call Your Doctor Call your doctor right away if you have any of the following: Confusion or forgetfulness Muscle spasms, cramping, or twitching Seizures Gait disturbances

  - 🔸 **<a id="medical-risk">2.3.3. Medical risk</a>**

    _Definition:_ Communication about the likelihood and severity of harm or negative consequences that can result from medical decisions or actions.

    _Example (fall):_

    - High risk for falls
    - I am worried about falling.

  - 🔸 **<a id="patient-education">2.3.4. Patient education</a>**

    _Definition:_ Clinical language about providing patients with information, knowledge, and resources to help them understand their medical conditions, treatment options, and self-care practices.

    _Example (fall, delirium):_

    - Fall prevention education
    - The nurse disconnected the call

- 📄 **<a id="section">2.4. Section</a>**

  _Definition:_ (Structure of clinical document e.g., Clinical Document Architecture HL7 standard): Section errors occur when NLP models falsely capture the pre-defined concepts that belong to the wrong section.

  _Example (delirium):_

  - Family History (Section ID)
  - Hypertension: Yes
  - Diabetes: Yes
    \*Family information sometimes is considered as exclusion. Failure to consider the section information can result in misclassification.

- 📄 **<a id="temporal-status">2.5. Temporal Status</a>**

  _Definition:_ Temporal status refers to the current condition or state of a patient's medical or health-related information. It is used to distinguish between historical information (past status) and information that reflects the patient's current state (present status).

  - 🔸 **<a id="history">2.5.1. History</a>**

    _Example (delirium):_

    - Patient has a history of hallucinations (past)
    - Patient described episodes of delirium several years ago (past)
    - His hallucinations were resolved (past)

  - 🔸 **<a id="present">2.5.2. Present</a>**

    _Example (delirium):_

    - Patient experienced an episode of confusion this morning (current)
    - Currently CAM Positive (current)
    - She has experienced confusion several times during the last few days (current/past)

- 📄 **<a id="subject">2.6. Subject</a>**

  _Definition:_ An individual or entity that is the focus of attention or observation to be identified within a specific clinical context. The most common scenario is to refer to an individual who is receiving medical treatment.

  - 🔸 **<a id="family-member">2.6.1. Family member</a>**

    _Definition:_ Family members can be subjects of the study when their medical history, genetic information, or other factors are relevant to the research or medical care of the patient. The description can be commonly found in the family history section of clinical notes.

    _Example (delirium):_

    - Patient’s grandpa has hypertension and diabetes (FP)
    - Daughter/Son called and states patient has continued to be confused (TP)

  - 🔸 **<a id="other-subject">2.6.2. Other subject</a>**

    _Definition:_ The target subject can also be non-human, such as disease symptoms.

    _Example (delirium):_

    - The character of symptoms is agitated.
    - The course/duration of symptoms is fluctuating in intensity.
    - The vision he says has been very blurry and it fluctuates.

**<a id="linguistic-error">📂 3. Linguistic Error</a>**

_Definition:_ Linguistic errors refer to inaccuracies or inconsistencies in the representation of clinical expressions, including issues related to morphology, orthography, semantics, and syntax. These errors can lead to misclassification and occur more frequently in false negative expressions.

- 📄 **<a id="morphological-error">3.1. Morphological error</a>**

  _Definition:_ Morphologic errors occur when NLP models fail to capture the pre-defined concepts due to the variation in the structure and formation of words (prefixes, suffixes, and base words).

  _Example (delirium):_

  - Hallucinates; Hallucination;
  - Altered; Alteration; Alter

- 📄 **<a id="orthographic-error">3.2. Orthographic error</a>**

  _Definition:_ Orthographic errors occur when NLP models fail to capture the pre-defined concepts due to the variation in language conventions including special characters, spelling, hyphenation, capitalization, word breaks, emphasis, and punctuation.

  - 🔸 **<a id="spelling-error">3.2.1. Spelling error</a>**

    _Definition:_ A spelling error occurs when a deviation from the standard or intended spelling convention of the language leads to misclassification for the model.

    _Example (delirium; fall):_

    - Decresed (Decreased) responsiveness
    - agitated (agitated)
    - ell (Fell) last night

  - 🔸 **<a id="abbreviation-error">3.2.2. Abbreviation error</a>**

    _Definition:_ An abbreviation error occurs when the model misinterprets or fails to recognize abbreviated forms of words or phrases.

    _Example:_

    - COPD - Chronic Obstructive Pulmonary Disease
    - UTI - Urinary Tract Infection
    - GERD - Gastroesophageal Reflux Disease
    - DM - Diabetes Mellitus

- 📄 **<a id="semantic-error">3.3. Semantic error</a>**

  _Definition:_ A semantic error occurs when the meaning or interpretation of a clinical text is misunderstood by the model or annotator. Common semantic error types include homonyms, implied inference, statistical inference, and synonym.

  - 🔸 **<a id="homonyms">3.3.1. Homonyms</a>**

    _Definition:_ Words that are spelled and pronounced the same but have different meanings.

    _Example (fall):_

    - Fall asleep
    - Redwood falls
    - Water falls

  - 🔸 **<a id="implied-inference">3.3.2. Implied inference</a>**

    _Definition:_ Missing paraphrase and implication.

    _Example (fall):_

    - landing flat on his back
    - missed the last step while going down the stairs
    - patient went down with a sudden knee flexion

    _Example (delirium):_

    - Becoming more forgetful
    - Difficulty with his/her speech particularly with word finding
      -> Concepts or expressions that can directly/indirectly infer the target concept of interest

  - 🔸 **<a id="statistical-inference">3.3.3. Statistical inference</a>**

    _Definition:_ Inability to make proper statistical inference. Common examples include rare expressions that, although occurring in the training data, the model is still unable to fully capture all possible cases.

    _Example (fall):_

    - Common expression: patient fell.
    - Rare expression: when he went down, his hands were behind him.

  - 🔸 **<a id="synonym">3.3.4. Synonym</a>**

    _Definition:_ Missing new lexicon and synonyms not in the original NLP ruleset.

    _Example (delirium):_

    - Disorganized thinking: fuzziness; obtunded; forgetful
    - Difficulty concentrating: inattention
    - Disconnected: obtunded; fatigue; somnolence

- 📄 **<a id="syntactic-error">3.4. Syntactic error</a>**

  _Definition:_ A syntactic error occurs when violating the grammatical structure or rules of the language, especially when the system fails to parse or understand the grammatical structure of sentences or phrases correctly.

  - 🔸 **<a id="sentence-boundaries">3.4.1. Sentence boundaries</a>**

    _Definition:_ Sentence boundary detection is a task of segmenting individual sentences within a block of clinical text. Imperfect sentence boundaries, due to the lack of punctuation, can cause errors for sentence-level classifiers or extractors.

    _Example (fall):_

    - Patient did not have dementia; but had several syncope events.

- 📄 **<a id="typographical-error">3.5. Typographical error</a>**

  _Definition:_ Typographical errors occur when NLP models fail to capture the pre-defined concepts due to the variation in the physical representation and appearance of text. Common typographical representations include inserting, deleting, replacing, and transposing the original word form and format.

  _Example:_

  - Randcom (insert)
  - Randm (delete)
  - Randcm (replace)
  - Randmo (transpose)

</details>

**<a id="logic-error">📂 4. Logic Error</a>**

_Definition:_ Logic errors occur when the NLP model falsely makes a classification or summarization due to logic or rule patterns.

- 📄 **<a id="logic-pattern-and-rule">4.1. Logic, pattern, and rule</a>**

  _Definition:_ Logic errors occur when the NLP model falsely makes a classification or summarization due to logic or rule patterns.

  _Example (SBI, delirium):_

  - Silent cerebrovascular disease = positive mention of brain infarction
  - **Correction:** positive mention of brain infarction without prior history of stroke
  - CAM Delirium positive = CAM_BCD
    **Correction:** CAM Delirium positive = CAM_ABCD or CAM_ABC or CAM_ABD

**<a id="other-error">📂 5. Other Errors</a>**

- 📄 **<a id="incomplete-extraction">5.1. Incomplete extraction</a>**

  _Definition:_ The NLP model can only partially identify a concept, which cannot provide a complete picture for ascertaining a patient's status.

  _Example (WMD):_

  - Model only correctly captured disease and failed to identify grading: Punctate foci (grading) deep white matter (disease) lesion found.

- 📄 **<a id="dictionary-error">5.2. Dictionary error</a>**

  _Definition:_ An error made by a middleware dictionary or knowledge base such as the Unified Medical Language System (UMLS) and MeSH (Medical Subject Headings).

  _Example:_

  - UMLS synonymy error
  - UMLS absence error

- 📄 **<a id="normalization-error">5.3. Normalization error</a>**

  _Definition:_ An error occurred while mapping medical mentions to standardized ontologies like UMLS or controlled vocabularies like SNOMED CT.

  _Example:_

  - In UMLS, some medications' descriptions contain strength information, including "cyanocobalamin 1000 MCG Oral Tablet" (CUI: C0976004), "cyanocobalamin 1000 MCG Oral Capsule" (CUI: C0786262), etc. Based on the example: "2. Cyanocobalamin 1000 mcg/mL Solution Sig: One (1) Injection DAILY (Daily) for 3 days," the system matched "Cyanocobalamin 1000" to CUI-C0976004 as a medication and ignored "1000 mcg/ml" as a strength.
