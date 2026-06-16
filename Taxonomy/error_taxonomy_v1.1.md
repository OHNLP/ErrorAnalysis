### Summary of Common Error Types for EHR-based Clinical Concept Extraction

| **Error Dimension** | **Error Class** | **Error Sub-Class** |
| --- | --- | --- |
| 1\. Annotation Error | 1.1. Missing annotation | N/A |
| | 1.2. Guideline error | N/A |
| | 1.3. Misclassification | N/A |
| | 1.4. Omission | N/A |
| 2\. Contextual Error | 2.1. Absence of context | N/A |
| | | Context length |
| | 2.2. Certainty | 2.2.1. Differential diagnosis |
| | | 2.2.2. Hypothetical language |
| | | 2.2.3. Medical grading |
| | | 2.2.4. Negation |
| | | 2.2.5. Possible and probable language |
| | | 2.2.6. Distortion |
| | 2.3. Exclusion | 2.3.1. Medical evaluation |
| | | 2.3.2. Medical instruction |
| | | 2.3.3. Medical risk |
| | | 2.3.4. Patient education |
| | 2.4. Section | N/A |
| | 2.5. Temporal Status | 2.5.1 History |
| | | 2.5.2 Present |
| | 2.6. Subject | 2.6.1 Family member |
| | | 2.6.2 Family history |
| | | 2.6.3 Other subject |
| 3\. Linguistic | 3.1. Morphological error | N/A |
| | 3.2. Orthographic error | 3.2.1. Spelling error |
| | | 3.2.2. Abbreviation error |
| | 3.3. Semantic error | 3.3.1. Conflation |
| | | 3.3.2. Homonyms |
| | | 3.3.3. Implied inference |
| | | 3.3.4. Partially correct |
| | | 3.3.5. Statistical inference |
| | | 3.3.6. Synonym |
| | 3.4. Syntactic error | 3.4.1. Sentence boundaries |
| | 3.5. Typographical error | N/A |
| 4\. Logic Error | 4.1. Complete hallucination | N/A |
| | 4.2. Logic, pattern, and rule | N/A |
| | 4.3. Instruction following failure | N/A |
| | 4.4. Overextraction | N/A |
| 5\. Output / Generation Error | 5.1. Verbosity and format error | N/A |
| | 5.2. Consistency error | N/A |
| | 5.3. Sycophantic error | N/A |
| 6\. Other Error | 6.1. Incomplete extraction | N/A |
| | 6.2. Dictionary error | N/A |
| | 6.3. Normalization error | N/A |


### Definition of Error Taxonomy

1. **Annotation error:** Human error occurred during corpus annotation, which is a process involving the manual review, judgment, marking, and labeling of linguistic and clinical concepts from unstructured text.
    1. **Missing annotation:** annotators fail to capture concepts due to human errors

Example (delirium):

- Confusion/Disorientation Hendrich: Yes
- Best Verbal Response Glasgow: Confused
    1. **Annotation guideline:** errors occur due to conflicts between NLP definition and annotation guideline definition. E.g., the version of guideline does not align with NLP version.

Example (delirium):

- Guideline definition: encephalopathy = delirium positive

NLP definition: encephalopathy = CAM_D

    1. **Misclassification:** Annotator captured incorrect concepts due to human errors

Example (delirium):

- Screening for delirium = delirium (positive)

\*Incorrect, screening for delirium should mark as delirium (exclusion)

    1. **Omission:** The model fails entirely to produce output for a concept that is clearly present in the text. Distinct from Missing Annotation (1.1), which applies to human gold-standard labels; Omission applies to model output.

Example (fall):

- Note: "Patient fell"
- Model outputs: no results

2. **Contextual error:** information found in the context of the condition that modifies individual clinical conditions.
    1. **Absence of context:** NLP model falsely or partially captures concepts due to lack of enough context to determine the certainty, status and subject of the expression

Example (delirium):

- 'Confusion' (occurs as a single concept without context)

Correction:

- Patient has a constant confused look displayed on his/her face.

        - **Context length:** The NLP/LLM model fails to interpret a concept correctly because the relevant contextual information extends beyond its processing window — such as a preceding sentence, prior paragraph, or token-limit boundary. The model processes only a fragment and draws an incorrect conclusion from the partial view.

Example (delirium):

- Sentence 1: "The patient was alert and oriented earlier."
- Sentence 2: "Later became confused overnight."
- Model processes only Sentence 1 → incorrectly concludes no delirium present.

    1. **Certainty:** NLP model falsely captures concepts due to incorrectly judging grade (within the power or capacity of someone or something), possible, probable-related terms or expressions
        1. **Differential diagnosis:** description that document a process where clinicians consider various possible conditions or diseases that could explain a patient's symptoms before making a final diagnosis.

Example (SBI):

- One potential differential diagnosis for silent infarction could include other causes of neurological symptoms such as migraine with aura, transient ischemic attack (TIA), or small fiber neuropathy
        1. **Hypothetical language:** hypothesis-related concepts or expressions.

Example (delirium):

- Patient would have delirium if the CAM screening test come out positive
        1. **Medical Grading:** A model incorrectly classifies concepts due to an erroneous assessment of grade, which pertains to the ability or capacity of someone or something.

Example (WMD):

- Moderate scattered deep and subcortical punctate white matter
- Abnormal low- density in the right parietal periventricular white matter
        1. **Negation:** NLP model falsely captures concepts due to incorrectly judging negation-related (contradiction or denial of something) terms or expressions.

Example (delirium):

- Not able to be easily aroused
- Patient does not have encephalopathy.
- No history of confusion
        1. **Possible and probable language:** NLP model falsely captures concepts due to incorrectly possible, probable-related terms or expressions.

Example (WMD):

- Likely/probable focus of nonspecific white matter disease
- Possibility of demyelinating disease
        1. **Distortion:** The model misrepresents the temporal, certainty, or intensity dimension of a valid concept that is actually present in the text. Unlike Negation or Possible/Probable errors where the concept is absent or uncertain, here the concept is confirmed but its characterization is warped. LLMs are particularly prone to this due to probabilistic generation.

Example:

- Temporal – "Patient had confusion" → NLP model outputs "Current confusion present"
- Certainty – "Possible delirium noted" → NLP model outputs "Positive for delirium"
- Intensity – "Mild confusion observed" → NLP model outputs "Severe confusion"

    1. **Exclusion:** NLP model falsely captures concepts due to the concepts occur in a wrong context
        1. **Medical evaluation:** A description of a patient presenting to a clinic for evaluation and assessment of their condition. The concepts need to be excluded because they do not reflect patient's disease status

Example (delirium):

- I was called to evaluate the patient for an episode of confusion
- Patient was screened for confusion
        1. **Medical instruction:** communication of medical information, advice, and instructions to individuals seeking healthcare or treatment.

Example (delirium):

- When to Call Your Doctor Call your doctor right away if you have any of the following: Confusion or forgetfullness Muscle spasms, cramping, or twitching Seizures Gait disturbances
        1. **Medical risk:** communication about the likelihood and severity of harm or negative consequences that can result from medical decisions or actions.

Example (fall):

- High risk for falls
- I am worried about falling.
        1. **Patient education:** clinical language about providing patients with information, knowledge, and resources to help them understand their medical conditions, treatment options, and self-care practices.

Example (fall, delirium):

- Fall prevention education
- The nurse disconnected the call
    1. **Section:** (structure of clinical document e.g., Clinical Document Architecture HL7 standard): section errors occur when NLP models falsely captures the pre-defined concepts that belongs to wrong section.

Example (delirium):

- Family History (Section ID)

Hypertension: Yes

Diabetes: Yes

\*Family information sometimes is considered as exclusion. Fail to consider the section information can result in misclassification.

    1. **Temporal Status:** temporal status refer to the current condition or state of a patient's medical or health-related information. It is used to distinguish between historical information (past status) and information that reflects the patient's current state (present status).
        1. **History**

Example (delirium):

- Patient has history of hallucinations (past)
- Patient described episodes of delirium several years ago (past)
- His hallucinations were resolved (past)
        1. **Present**

Example (delirium):

- Patient experienced episode of confusion this morning (current)
- Currently CAM Positive (current)
- She has experienced confusion several times during the last few days (current/past)
    1. **Subject:** an individual or entity that is the focus of attention or observation to be identified within a specific clinical context. Most common scenario is to refer to an individual who is receiving medical treatment.
        1. **Family member:** family member can be subjects of the study when their medical history, genetic information, or other factors are relevant to the research or medical care of the patient. The description can be commonly found in the family history section of clinical notes.

Example (delirium):

- Patient's grandpa has hypertension and diabetes (FP)
- Daughter/Son called and states patient has continued to be confused (TP)
        1. **Family history:** The NLP/LLM model incorrectly attributes a condition documented in a family history entry to the index patient. LLMs may conflate "documented in the note" with "belonging to the patient" when generating summaries.

Example:

- Note: "Family history: Hypertension (mother)"
- Model output: "Patient has hypertension"
        1. **Other subject:** the target subject can also be non-human, such as disease symptoms.

Example (delirium):

- The character of symptoms is agitated.
- The course/duration of symptoms is fluctuating in intensity.
- The vision he says has been very blurry and it fluctuates.

3. **Linguistic error:** linguistic errors refer to inaccuracies or inconsistencies in the representation of clinical expressions, including issues related to morphology, orthography, semantics, and syntax. These errors can lead to misclassification and occur more frequently in false negative expressions
    1. **Morphological error:** morphologic errors occur when NLP models fails to capture the pre-defined concepts due to the variation in structure and formation of words (prefixes, suffixes and base words)

Example (delirium):

- Hallucinates; Hallucination;
- Altered; Alteration; Alter
    1. **Orthographic error:** orthographic errors occur when NLP models fail to capture the pre-defined concepts due to the variation in language conventions including special characters, spelling, hyphenation, capitalization, word breaks, emphasis, and punctuation.
        1. **Spelling error**: a spelling error occurs when a deviation from the standard or intended spelling convention of the language led to misclassification for the model.

Example (delirium; fall):

- Decresed (Decreased) responsiveness
- agitated (agitated)
- ell (Fell) last night
        1. **Abbreviation error**: an abbreviation error occurs when the model misinterprets or fails to recognize abbreviated forms of words or phrases.

Example:

- COPD - Chronic Obstructive Pulmonary Disease
- UTI - Urinary Tract Infection
- GERD - Gastroesophageal Reflux Disease
- DM - Diabetes Mellitus
    1. **Semantic error:** a semantic error occurs when the meaning or interpretation of a clinical text is misunderstood by model or annotator. Common semantic error types include homonyms, implied inference, statistical inference, and synonym.
        1. **Conflation:** The model merges two or more distinct clinical concepts into a single, less specific label, losing the nuance between related but different conditions. LLMs trained to summarize may be especially prone to collapsing granular distinctions.

Example:

- Text: "The patient has chronic confusion."
- Model output: delirium (positive)
- Correct label: dementia or chronic cognitive impairment — not acute delirium
        1. **Homonyms:** words that are spelled and pronounced the same but have different meanings.

Example (fall):

- Fall asleep
- Redwood falls
- Water falls
        1. **Implied inference:** missing paraphrase and implication.

Example (fall):

- landing flat on his back
- missed the last step while going down the stairs
- patient went down with a sudden knee flexion

Example (delirium):

- Becoming more forgetful
- Difficulty with his/her speech particularly with word finding

_\*Concepts or expressions that can directly/indirectly infer the target concept of interest_

        1. **Partially correct:** The model identifies a concept but captures it incompletely — missing a critical modifier such as negation, severity, or temporal qualifier — yielding a result that is directionally wrong despite partial recognition. Common in LLM zero-shot extraction where modifier scope is not enforced.

Example (delirium):

- Text: "No signs of delirium observed"
- Model output: delirium (positive)
- Error: Model recognized the concept but missed the negation modifier.
        1. **Statistical inference:** inability of make proper statistic inference. Common examples include rare expression although occurs in training data, the model still unable to fully capture all possible cases.

Example (fall):

- Common expression: patient fell.
- Rare expression: when he went down, his hands were behind him.
        1. **Synonym:** missing new lexicon and synonym not in the original NLP ruleset

Example (delirium):

- Disorganized thinking: fuzziness; obtunded; forgetful
- Difficulty concentrating: inattention
- Disconnected: obtunded; fatigue; somnolence
    1. **Syntactic error:** a syntactic error occurs when violating the grammatical structure or rules of the language especially when the system fails to parse or understand the grammatical structure of sentences or phrases correctly.
        1. **Sentence boundaries:** sentence boundary detection is a task of segmenting individual sentences within a block of clinical text. Imperfect sentence boundaries, due to the lack of punctuation, can cause errors for sentence-level classifiers or extractors.

Example (fall):

- Patient did not have dementia; but had several syncope events.
    1. **Typographical error**: typographical errors occur when NLP models fails to capture the pre-defined concepts due to the variation in the physical representation and appearance of text. Common typographical representations include inserting, deleting, replacing, and transposing the original word form and format.

Example:

- Randcom (insert)
- Randm (delete)
- Randcm (replace)
- Randmo (transpose)

4. **Logic error**: logic errors occur when NLP model falsely make classification or summarization due to logic or rule patterns.
    1. **Complete hallucination:** The NLP/LLM model generates a clinical concept or finding that is entirely absent from the source text, fabricating information based on learned associations rather than actual input. Unlike other error types where a concept is present but misclassified, hallucination introduces content with no grounding in the note. This is a distinctive failure mode of generative AI.

Example (fall):

- Note: "Patient walked to the restroom unaided."
- Model output: "Patient fell in the restroom."
- Error: Concept of a fall is entirely fabricated.
    1. **Logic pattern rule:** logic errors occur when NLP model falsely make classification or summarization due to logic or rule patterns.

Example (SBI, delirium):

- Silent cerebrovascular disease = positive mention of brain infarction
  - Correction: positive mention of brain infarction without prior history of stroke
- CAM Delirium positive = CAM_BCD
  - Correction: CAM Delirium positive = CAM_ABCD or CAM_ABC or CAM_ABD
    1. **Instruction following failure:** The LLM model fails to adhere to the extraction task instructions — such as output format constraints, concept scope restrictions, or structured output requirements — producing results that deviate from the specified protocol even when the relevant clinical content is present and processable.

Example:

- Instruction: "Extract only current-status diagnoses; exclude historical mentions."
- Model output includes: "History of delirium" (past, explicitly excluded)
- Instruction: "Return output as JSON with keys: concept, polarity, temporality."
- Model output: free-text narrative summary instead of structured JSON.
    1. **Overextraction:** The model extracts more concepts than specified — capturing semantically related but out-of-scope terms, broadly associated concepts, or neighboring concepts not matching the target definition. Common in LLMs given their tendency to be comprehensive rather than precise.

Example (delirium):

- Task: extract delirium-positive mentions.
- "Patient has dementia and showed confusion today." → Model extracts both dementia AND confusion as delirium-positive.
- Correct: only confusion (acute) qualifies; dementia is a distinct, excluded condition.

5. **Output / Generation Error:** A new error dimension specific to generative AI and LLM-based systems. These errors arise not from misclassification of clinical content per se, but from failures in *how* the model produces its output — including format deviations, cross-prompt inconsistency, and socially biased response shaping. These errors are not present in traditional rule-based NLP and represent a qualitatively different failure class for LLM adoption in clinical NLP pipelines.
    1. **Verbosity and format error:** The model produces output that is structurally non-compliant with the required format — including excessive verbosity, missing fields, extraneous narrative, malformed JSON/XML, or unexpected truncation. In clinical NLP pipelines where downstream processing depends on structured outputs, format errors cause pipeline failures independent of whether the underlying extraction was correct.

Example:

- Instruction: "Respond in JSON: {"concept": ..., "polarity": ..., "temporality": ...}"
- Model output: "The patient appears to be experiencing current episodes of confusion, which would indicate a positive finding for delirium at the present time."
- Error: Free-text narrative instead of required structured output.
    1. **Consistency error:** The LLM produces different extraction results for the same or semantically equivalent clinical text across separate runs, prompting sessions, or paraphrased inputs — without any change in the task instructions. This non-deterministic behavior undermines reproducibility, a critical requirement for clinical validation and multi-site deployment.

Example:

- Input: "Patient appeared confused and disoriented last night."
- Run 1 → delirium: positive
- Run 2 → delirium: uncertain
- Run 3 → delirium: negative
- Same input, same prompt → different polarity across runs.
    1. **Sycophantic error:** The LLM adjusts its extraction output in response to perceived user preferences, prior conversational context, or feedback cues — rather than strictly based on the clinical text. In multi-turn prompting or interactive annotation workflows, a model that "agrees" with user corrections regardless of text evidence introduces systematic bias.

Example:

- User: "Are you sure this is not delirium? Look again."
- Model (revised): "On reflection, yes, this does appear to be delirium."
- Error: No new clinical evidence provided — model changed output due to social pressure, not text.

6. **Other error**
    1. **Incomplete extraction:** the NLP model can only partially identify a concept, which cannot provide a complete picture for ascertaining a patient's status.

Example (WMD):

- Model only correctly captured disease and failed to identify grading: Punctate foci (grading) deep white matter (disease) lesion found.
    1. **Dictionary error**: an error made by a middleware dictionary or knowledge base such Unified Medical Language System (UMLS) and MeSH (Medical Subject Headings)

Example:

- UMLS synonymy error
- UMLS absence error
    1. **Normalization error**: An error occurred while mapping medical mentions to standardized ontologies like UMLS or controlled vocabularies like SNOMED CT.

Example:

- In UMLS, some medications' descriptions contain strength information, including "cyanocobalamin 1000 MCG Oral Tablet" (CUI: C0976004), "cyanocobalamin 1000 MCG Oral Capsule" (CUI: C0786262), etc. Based on the example: "2. Cyanocobalamin 1000 mcg/mL Solution Sig: One (1) Injection DAILY (Daily) for 3 days," the system matched "Cyanocobalamin 1000" to CUI-C0976004 as a medication and ignored "1000 mcg/ml" as a strength.
