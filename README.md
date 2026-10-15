### Design and Evaluation of an Intelligent Assessment Framework for Handwritten Examination Responses

> **EvalAI is a research-driven prototype exploring how AI can assist in evaluating handwritten examination responses without replacing human judgment.**

---

## Overview

Examination evaluation is fundamentally an exercise in judgment.

A teacher does not simply check whether a student's answer contains the same words as a reference answer. They interpret reasoning, recognize valid alternative explanations, award partial credit, and make decisions when an answer is ambiguous.

Yet evaluating large numbers of handwritten examination papers is time-consuming.

**EvalAI explores whether AI can assist with this process without removing the human judgment at its centre.**

The project investigates a pipeline combining:

- Handwritten text recognition
- Image preprocessing
- Semantic understanding
- Marking-scheme and rubric alignment
- Explainable scoring
- Confidence and uncertainty estimation
- Human-in-the-loop review

The goal is not to create a system that simply produces a number.

The goal is to explore whether AI can make assessment **more efficient while preserving the teacher's ability to interpret, question, and decide.**

---

## The Question Behind EvalAI

The project grew from a broader question about automation:

> **When technology can automate part of a skill, should it automatically replace the human judgment involved in that skill?**

In examination assessment, the answer is not straightforward.

A fully automated system could be efficient, but efficiency alone does not guarantee fairness or accuracy.

A student's answer may:

- use different wording from the marking scheme,
- contain valid reasoning expressed unconventionally,
- deserve partial credit,
- include diagrams or mathematical notation,
- be difficult for an AI system to interpret,
- or simply fall into a case where the correct decision is uncertain.

EvalAI therefore explores **assistance rather than replacement**.

---

## Problem Statement

Traditional examination evaluation has several challenges:

1. **Large volumes of handwritten responses** require substantial teacher time.
2. **Handwriting variability** makes automated text recognition difficult.
3. OCR or handwriting recognition errors can change the meaning of an answer.
4. Exact keyword matching can penalize valid alternative wording.
5. Scientific and mathematical responses often require contextual interpretation.
6. AI-generated scores without explanations are difficult to verify.
7. Ambiguous responses should not necessarily be forced into an automated decision.

EvalAI investigates whether a multimodal assessment framework can address these problems while keeping teachers involved in the final decision.

---

## Research Question

> **Can a multimodal AI-based assessment framework reliably evaluate handwritten STEM examination responses under CBSE-style marking schemes while preserving meaningful human oversight?**

### Supporting Questions

- How accurately can handwritten examination responses be converted into machine-readable representations?
- How does OCR/HTR error affect downstream assessment?
- Can semantic evaluation identify valid answers that use different wording from the reference answer?
- How can marking schemes be represented computationally?
- Can confidence estimation identify responses that require human review?
- Can explanations make AI-assisted marking more interpretable to teachers?
- At what point should an AI system defer rather than decide?

---

## Hypothesis

A multimodal assessment pipeline combining handwriting recognition, semantic evaluation, rubric alignment, and uncertainty estimation will provide more contextually meaningful assessment than keyword-based approaches.

However, ambiguous and low-confidence cases will still require human review.

---

## Core Principle

### AI should assist judgment, not silently replace it.

EvalAI is designed around four principles.

### 1. Accuracy Before Automation

A system that evaluates every answer but gets difficult cases wrong is less useful than one that knows when it is uncertain.

### 2. Explainability

A score should be accompanied by evidence showing how the response aligned with the marking criteria.

### 3. Human-in-the-Loop

Teachers remain the final authority.

The system should be able to say:

> **"I am uncertain. This response needs human review."**

rather than pretending every decision is equally reliable.

### 4. Semantic Fairness

Students should not be penalized simply because they express a correct idea differently from the wording used in a reference answer.

---

## Proposed System

```text
                 HANDWRITTEN ANSWER
                         │
                         ▼
              ┌─────────────────────┐
              │ Image Preprocessing │
              │       OpenCV        │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Handwriting / OCR   │
              │    Recognition      │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Structured Response │
              │   Representation    │
              └──────────┬──────────┘
                         │
             ┌───────────┴───────────┐
             ▼                       ▼
       Student Response        Marking Scheme
             │                       │
             └───────────┬───────────┘
                         ▼
              ┌─────────────────────┐
              │ Semantic Evaluation │
              │   + Rubric Logic    │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Score + Evidence    │
              │ + Confidence        │
              └──────────┬──────────┘
                         │
                  ┌──────┴──────┐
                  ▼             ▼
              Confident      Uncertain
                  │             │
                  ▼             ▼
             AI-assisted     Teacher
             assessment       review
```

---

## Why Semantic Evaluation?

One limitation of traditional automated marking is that it can become overly dependent on expected words.

Two students might communicate the same concept using substantially different wording.

A keyword-based system could interpret:

```text
Different wording
        ↓
Different answer
```

when the actual relationship is:

```text
Different wording
        ↓
Same underlying concept
```

EvalAI therefore explores semantic representations of student responses rather than relying solely on exact word matches.

---

## Multimodal AI

Handwritten examination assessment is not purely a text problem.

A response can contain:

- Handwritten text
- Mathematical expressions
- Equations
- Diagrams
- Symbols
- Spatial relationships
- Visual annotations
- Written reasoning

This creates a naturally multimodal problem.

The longer-term direction of EvalAI is therefore to move beyond:

```text
Image → OCR → Keyword Matching → Score
```

toward:

```text
Image
  ↓
Visual + Textual Understanding
  ↓
Structured Response
  ↓
Conceptual / Reasoning Evaluation
  ↓
Rubric Alignment
  ↓
Score + Evidence + Confidence
```

---

## Proposed Technology Stack

| Component | Proposed Technology |
|---|---|
| Prototype | Base44 |
| Image Processing | OpenCV |
| Handwriting Recognition | TrOCR / HTR models |
| Semantic Representation | Sentence-BERT / Transformer embeddings |
| Semantic Evaluation | Embedding similarity + rubric-based evaluation |
| Explainability | Evidence-based scoring explanations |
| Confidence | Confidence estimation + uncertainty thresholds |
| Version Control | Git / GitHub |
| Evaluation | Human-annotated examination responses |

### Prototype vs. Research Implementation

The current prototype was developed using **Base44 as a rapid prototyping environment**.

Base44 allowed the assessment workflow and user experience to be developed and tested before building the full machine-learning infrastructure.

The underlying research work is not limited to the interface.

The project includes the development of:

- the research question,
- assessment methodology,
- system architecture,
- rubric-based evaluation approach,
- explainability framework,
- uncertainty strategy,
- evaluation methodology,
- and planned experimental benchmarks.

The intended next stage is a more conventional ML implementation that can be independently evaluated and benchmarked.

---

## Evaluation Framework

EvalAI will ultimately be evaluated against human assessment rather than simply whether an AI-generated score appears plausible.

### Handwriting Recognition

Potential metrics:

- Character Error Rate (CER)
- Word Error Rate (WER)
- Recognition accuracy

### Assessment Performance

Potential metrics:

- Mean Absolute Error (MAE)
- Root Mean Square Error (RMSE)
- Correlation with human scores
- Exact mark agreement
- Agreement within an acceptable mark range

### Classification Performance

Where applicable:

- Precision
- Recall
- F1-score
- Accuracy

### Human-in-the-Loop Performance

Potential measurements include:

- Percentage of responses automatically assessed
- Percentage referred for teacher review
- Accuracy of high-confidence assessments
- Accuracy of low-confidence assessments
- Teacher agreement with AI-generated explanations
- Change in teacher evaluation time

---

## Baselines

The system can be compared against progressively more sophisticated approaches.

### Baseline 1: Exact Matching

Checks whether expected phrases occur in the response.

### Baseline 2: Keyword Matching

Uses predefined keywords associated with marking points.

### Baseline 3: Semantic Similarity

Uses transformer embeddings to compare student and reference responses.

### Baseline 4: Rubric-Aware Semantic Evaluation

Evaluates individual marking points using semantic similarity and rubric constraints.

### Proposed Framework

Combines:

- Handwriting recognition
- Semantic evaluation
- Rubric alignment
- Explainability
- Confidence estimation
- Human review

This progression allows the project to test whether each additional layer actually contributes to assessment quality.

---

## Explainability

EvalAI is not intended to output an unexplained score.

Instead of:

```text
Score: 2/3
```

the system should aim to produce something closer to:

```text
Score: 2/3

Identified:
✓ Correct definition
✓ Correct relationship between variables

Missing:
✗ Required explanation of the physical mechanism

Confidence:
High
```

The explanation provides a teacher with something to inspect rather than requiring blind trust in the model.

---

## Confidence and Uncertainty

A central part of the system is knowing when **not** to make a confident decision.

Potential uncertainty indicators include:

- Poor handwriting recognition
- Missing or unreadable text
- Conflicting semantic signals
- Responses outside the expected conceptual scope
- Ambiguous reasoning
- Diagrams requiring interpretation
- Low model confidence

The intended behaviour is:

```text
                 Response
                    │
                    ▼
             AI assessment
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
    High confidence      Low confidence
          │                   │
          ▼                   ▼
    AI-assisted          Teacher review
     decision
```

The goal is **selective automation**, not maximum automation.

---

## Current Prototype

The current EvalAI prototype was developed using **Base44** to validate the assessment workflow and user experience.

The prototype is intentionally an early-stage research artifact rather than a finished automated grading engine.

It demonstrates the direction of the system while leaving the underlying recognition, semantic evaluation, uncertainty calibration, and benchmarking as areas for continued research.

### Prototype

[EvalAI Prototype](https://grinning-eval-grade-flow.base44.app/)

---

## Research Workflow

```text
Literature Review
       ↓
Problem Definition
       ↓
Research Question
       ↓
System Design
       ↓
Prototype
       ↓
Dataset Development
       ↓
Baseline Experiments
       ↓
Model Development
       ↓
Evaluation
       ↓
Error Analysis
       ↓
Human-in-the-Loop Testing
       ↓
Iteration
```

---

## Dataset

The intended evaluation dataset will consist of handwritten examination responses paired with:

- Question
- Student response
- Reference answer
- Marking scheme
- Human-assigned score
- Relevant marking points
- Optional teacher comments
- AI-generated score
- AI confidence
- AI explanation

A key requirement is preserving the distinction between:

**surface-level wording** and **underlying conceptual correctness**.

The dataset should therefore contain multiple valid formulations of concepts wherever possible.

---

## Error Analysis

A major part of the research is understanding **why the system fails**.

Potential error categories include:

### Recognition Errors

The handwriting is incorrectly transcribed.

### Semantic Errors

The system incorrectly interprets the student's meaning.

### Rubric Errors

A valid concept is present but is not correctly mapped to a marking point.

### Reasoning Errors

The system identifies relevant terminology but fails to understand an incorrect logical relationship.

### Over-Marking

The system awards marks when the response does not satisfy the required criterion.

### Under-Marking

The system fails to recognize a valid alternative explanation.

### Confidence Errors

The system is highly confident despite being incorrect.

Error analysis will be used to determine where improvements are actually necessary rather than optimizing only for a single aggregate score.

---

## Scope

The initial research scope focuses on structured STEM examinations, particularly:

- Physics
- Chemistry
- Mathematics

The framework is designed around examinations with defined marking schemes and marks allocated to specific concepts, steps, or reasoning.

Expansion to additional subjects would require separate evaluation rather than assuming that a model validated on STEM responses will generalize automatically.

---

## Ethical Considerations

Automated examination assessment has direct implications for fairness.

EvalAI therefore treats automated scoring as **decision support rather than autonomous judgment**.

Key considerations include:

- Student privacy
- Bias in handwriting recognition
- Accessibility
- Language variation
- Different valid answer formulations
- Transparency of scoring
- Secure handling of examination data
- Human oversight

The system should not penalize a student simply because their handwriting or wording differs from the examples used during development.

---

## Limitations

EvalAI currently has several limitations:

1. Handwriting recognition can introduce downstream errors.
2. Scientific and mathematical notation can be difficult to interpret.
3. Semantic similarity does not automatically establish conceptual correctness.
4. Marking schemes can contain implicit teacher judgment that is difficult to formalize.
5. Human grading itself can vary between evaluators.
6. Small datasets may not represent the full diversity of student responses.
7. Automated assessment should not be assumed to generalize across subjects without independent evaluation.
8. A prototype interface does not by itself demonstrate that the underlying AI is accurate.

These limitations are part of the research problem rather than being hidden from the system design.

---

## Current Status

### Completed

- [x] Problem definition
- [x] Research question
- [x] Initial literature review
- [x] System concept
- [x] Assessment workflow
- [x] Initial prototype

### In Development

- [ ] Full multimodal model integration
- [ ] Dataset construction
- [ ] Human-annotated evaluation dataset
- [ ] Baseline experiments
- [ ] OCR/HTR benchmarking
- [ ] Semantic evaluation benchmarking
- [ ] Confidence calibration
- [ ] Human-vs-AI evaluation
- [ ] Full custom implementation

---

## Future Work

Future versions of EvalAI may investigate:

- Vision-language models for multimodal assessment
- Mathematical expression recognition
- Diagram understanding
- Question-aware grading
- Rubric generation and validation
- Confidence calibration
- Active learning from teacher corrections
- Teacher dashboards
- Large-scale human evaluation
- Cross-subject generalization
- Reproducible benchmarking
- A full Python-based ML implementation

---

## Repository Structure

The repository is intended to evolve toward:

```text
EvalAI/
│
├── README.md
│
├── docs/
│   ├── research-proposal.md
│   ├── system-architecture.md
│   ├── methodology.md
│   └── literature-review.md
│
├── src/
│   ├── preprocessing/
│   ├── ocr/
│   ├── semantic_evaluation/
│   ├── rubric/
│   ├── confidence/
│   └── explainability/
│
├── data/
│   └── README.md
│
├── experiments/
│   ├── baselines/
│   └── evaluation/
│
├── results/
│
├── assets/
│   └── screenshots/
│
├── requirements.txt
│
└── LICENSE
```

The repository structure will evolve as the project moves from prototype development toward reproducible research.

---

## Project Direction

EvalAI is ultimately built around a distinction:

```text
Automation ≠ Understanding
```

A useful assessment system should not simply ask:

> **"Did the student use the expected words?"**

It should move toward:

> **"Did the student's response demonstrate the concepts required by the marking scheme?"**

And when the answer is unclear:

> **"Should the system make this decision at all?"**

That final question is central to the project.

EvalAI therefore explores not only **how much assessment can be automated**, but **where automation should stop**.

---

## Author

**Gianna Binesh**

Student researcher interested in:

- Artificial Intelligence
- Multimodal AI
- Natural Language Processing
- Robotics
- Intelligent Systems
- Human-AI Interaction
- Educational Technology

---

## Acknowledgements

EvalAI is being developed as an independent research and engineering project exploring practical applications of AI in educational assessment.

---

## License

License information will be added as the project moves toward a reproducible public implementation.

---

## Disclaimer

EvalAI is a research project and prototype.

It is **not intended to replace qualified teachers or official examination evaluation systems**.

Automated outputs should be treated as assistive assessments and subject to human review, particularly for ambiguous or low-confidence responses.
"""

path = "/mnt/data/README.md"
pypandoc.convert_text(md, "md", format="md", outputfile=path, extra_args=["--standalone"])
print(path)

from pathlib import Path

md = """# EvalAI

### Design and Evaluation of an Intelligent Assessment Framework for Handwritten Examination Responses

> **EvalAI is a research-driven prototype exploring how AI can assist in evaluating handwritten examination responses without replacing human judgment.**

---

## Overview

Examination evaluation is fundamentally an exercise in judgment.

A teacher does not simply check whether a student's answer contains the same words as a reference answer. They interpret reasoning, recognize valid alternative explanations, award partial credit, and make decisions when an answer is ambiguous.

Yet evaluating large numbers of handwritten examination papers is time-consuming.

**EvalAI explores whether AI can assist with this process without removing the human judgment at its centre.**

The project investigates a pipeline combining:

- Handwritten text recognition
- Image preprocessing
- Semantic understanding
- Marking-scheme and rubric alignment
- Explainable scoring
- Confidence and uncertainty estimation
- Human-in-the-loop review

The goal is not to create a system that simply produces a number.

The goal is to explore whether AI can make assessment **more efficient while preserving the teacher's ability to interpret, question, and decide.**

---

## The Question Behind EvalAI

The project grew from a broader question about automation:

> **When technology can automate part of a skill, should it automatically replace the human judgment involved in that skill?**

In examination assessment, the answer is not straightforward.

A fully automated system could be efficient, but efficiency alone does not guarantee fairness or accuracy.

A student's answer may:

- use different wording from the marking scheme,
- contain valid reasoning expressed unconventionally,
- deserve partial credit,
- include diagrams or mathematical notation,
- be difficult for an AI system to interpret,
- or simply fall into a case where the correct decision is uncertain.

EvalAI therefore explores **assistance rather than replacement**.

---

## Problem Statement

Traditional examination evaluation has several challenges:

1. **Large volumes of handwritten responses** require substantial teacher time.
2. **Handwriting variability** makes automated text recognition difficult.
3. OCR or handwriting recognition errors can change the meaning of an answer.
4. Exact keyword matching can penalize valid alternative wording.
5. Scientific and mathematical responses often require contextual interpretation.
6. AI-generated scores without explanations are difficult to verify.
7. Ambiguous responses should not necessarily be forced into an automated decision.

EvalAI investigates whether a multimodal assessment framework can address these problems while keeping teachers involved in the final decision.

---

## Research Question

> **Can a multimodal AI-based assessment framework reliably evaluate handwritten STEM examination responses under CBSE-style marking schemes while preserving meaningful human oversight?**

### Supporting Questions

- How accurately can handwritten examination responses be converted into machine-readable representations?
- How does OCR/HTR error affect downstream assessment?
- Can semantic evaluation identify valid answers that use different wording from the reference answer?
- How can marking schemes be represented computationally?
- Can confidence estimation identify responses that require human review?
- Can explanations make AI-assisted marking more interpretable to teachers?
- At what point should an AI system defer rather than decide?

---

## Hypothesis

A multimodal assessment pipeline combining handwriting recognition, semantic evaluation, rubric alignment, and uncertainty estimation will provide more contextually meaningful assessment than keyword-based approaches.

However, ambiguous and low-confidence cases will still require human review.

---

## Core Principle

### AI should assist judgment, not silently replace it.

EvalAI is designed around four principles.

### 1. Accuracy Before Automation

A system that evaluates every answer but gets difficult cases wrong is less useful than one that knows when it is uncertain.

### 2. Explainability

A score should be accompanied by evidence showing how the response aligned with the marking criteria.

### 3. Human-in-the-Loop

Teachers remain the final authority.

The system should be able to say:

> **"I am uncertain. This response needs human review."**

rather than pretending every decision is equally reliable.

### 4. Semantic Fairness

Students should not be penalized simply because they express a correct idea differently from the wording used in a reference answer.

---

## Proposed System

```text
                 HANDWRITTEN ANSWER
                         │
                         ▼
              ┌─────────────────────┐
              │ Image Preprocessing │
              │       OpenCV        │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Handwriting / OCR   │
              │    Recognition      │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Structured Response │
              │   Representation    │
              └──────────┬──────────┘
                         │
             ┌───────────┴───────────┐
             ▼                       ▼
       Student Response        Marking Scheme
             │                       │
             └───────────┬───────────┘
                         ▼
              ┌─────────────────────┐
              │ Semantic Evaluation │
              │   + Rubric Logic    │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Score + Evidence    │
              │ + Confidence        │
              └──────────┬──────────┘
                         │
                  ┌──────┴──────┐
                  ▼             ▼
              Confident      Uncertain
                  │             │
                  ▼             ▼
             AI-assisted     Teacher
             assessment       review
```

---

## Why Semantic Evaluation?

One limitation of traditional automated marking is that it can become overly dependent on expected words.

Two students might communicate the same concept using substantially different wording.

A keyword-based system could interpret:

```text
Different wording
        ↓
Different answer
```

when the actual relationship is:

```text
Different wording
        ↓
Same underlying concept
```

EvalAI therefore explores semantic representations of student responses rather than relying solely on exact word matches.

---

## Multimodal AI

Handwritten examination assessment is not purely a text problem.

A response can contain:

- Handwritten text
- Mathematical expressions
- Equations
- Diagrams
- Symbols
- Spatial relationships
- Visual annotations
- Written reasoning

This creates a naturally multimodal problem.

The longer-term direction of EvalAI is therefore to move beyond:

```text
Image → OCR → Keyword Matching → Score
```

toward:

```text
Image
  ↓
Visual + Textual Understanding
  ↓
Structured Response
  ↓
Conceptual / Reasoning Evaluation
  ↓
Rubric Alignment
  ↓
Score + Evidence + Confidence
```

---

## Proposed Technology Stack

| Component | Proposed Technology |
|---|---|
| Prototype | Base44 |
| Image Processing | OpenCV |
| Handwriting Recognition | TrOCR / HTR models |
| Semantic Representation | Sentence-BERT / Transformer embeddings |
| Semantic Evaluation | Embedding similarity + rubric-based evaluation |
| Explainability | Evidence-based scoring explanations |
| Confidence | Confidence estimation + uncertainty thresholds |
| Version Control | Git / GitHub |
| Evaluation | Human-annotated examination responses |

### Prototype vs. Research Implementation

The current prototype was developed using **Base44 as a rapid prototyping environment**.

Base44 allowed the assessment workflow and user experience to be developed and tested before building the full machine-learning infrastructure.

The underlying research work is not limited to the interface.

The project includes the development of:

- the research question,
- assessment methodology,
- system architecture,
- rubric-based evaluation approach,
- explainability framework,
- uncertainty strategy,
- evaluation methodology,
- and planned experimental benchmarks.

The intended next stage is a more conventional ML implementation that can be independently evaluated and benchmarked.

---

## Evaluation Framework

EvalAI will ultimately be evaluated against human assessment rather than simply whether an AI-generated score appears plausible.

### Handwriting Recognition

Potential metrics:

- Character Error Rate (CER)
- Word Error Rate (WER)
- Recognition accuracy

### Assessment Performance

Potential metrics:

- Mean Absolute Error (MAE)
- Root Mean Square Error (RMSE)
- Correlation with human scores
- Exact mark agreement
- Agreement within an acceptable mark range

### Classification Performance

Where applicable:

- Precision
- Recall
- F1-score
- Accuracy

### Human-in-the-Loop Performance

Potential measurements include:

- Percentage of responses automatically assessed
- Percentage referred for teacher review
- Accuracy of high-confidence assessments
- Accuracy of low-confidence assessments
- Teacher agreement with AI-generated explanations
- Change in teacher evaluation time

---

## Baselines

The system can be compared against progressively more sophisticated approaches.

### Baseline 1: Exact Matching

Checks whether expected phrases occur in the response.

### Baseline 2: Keyword Matching

Uses predefined keywords associated with marking points.

### Baseline 3: Semantic Similarity

Uses transformer embeddings to compare student and reference responses.

### Baseline 4: Rubric-Aware Semantic Evaluation

Evaluates individual marking points using semantic similarity and rubric constraints.

### Proposed Framework

Combines:

- Handwriting recognition
- Semantic evaluation
- Rubric alignment
- Explainability
- Confidence estimation
- Human review

This progression allows the project to test whether each additional layer actually contributes to assessment quality.

---

## Explainability

EvalAI is not intended to output an unexplained score.

Instead of:

```text
Score: 2/3
```

the system should aim to produce something closer to:

```text
Score: 2/3

Identified:
✓ Correct definition
✓ Correct relationship between variables

Missing:
✗ Required explanation of the physical mechanism

Confidence:
High
```

The explanation provides a teacher with something to inspect rather than requiring blind trust in the model.

---

## Confidence and Uncertainty

A central part of the system is knowing when **not** to make a confident decision.

Potential uncertainty indicators include:

- Poor handwriting recognition
- Missing or unreadable text
- Conflicting semantic signals
- Responses outside the expected conceptual scope
- Ambiguous reasoning
- Diagrams requiring interpretation
- Low model confidence

The intended behaviour is:

```text
                 Response
                    │
                    ▼
             AI assessment
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
    High confidence      Low confidence
          │                   │
          ▼                   ▼
    AI-assisted          Teacher review
     decision
```

The goal is **selective automation**, not maximum automation.

---

## Current Prototype

The current EvalAI prototype was developed using **Base44** to validate the assessment workflow and user experience.

The prototype is intentionally an early-stage research artifact rather than a finished automated grading engine.

It demonstrates the direction of the system while leaving the underlying recognition, semantic evaluation, uncertainty calibration, and benchmarking as areas for continued research.

### Prototype

[EvalAI Prototype](https://grinning-eval-grade-flow.base44.app/)

---

## Research Workflow

```text
Literature Review
       ↓
Problem Definition
       ↓
Research Question
       ↓
System Design
       ↓
Prototype
       ↓
Dataset Development
       ↓
Baseline Experiments
       ↓
Model Development
       ↓
Evaluation
       ↓
Error Analysis
       ↓
Human-in-the-Loop Testing
       ↓
Iteration
```

---

## Dataset

The intended evaluation dataset will consist of handwritten examination responses paired with:

- Question
- Student response
- Reference answer
- Marking scheme
- Human-assigned score
- Relevant marking points
- Optional teacher comments
- AI-generated score
- AI confidence
- AI explanation

A key requirement is preserving the distinction between:

**surface-level wording** and **underlying conceptual correctness**.

The dataset should therefore contain multiple valid formulations of concepts wherever possible.

---

## Error Analysis

A major part of the research is understanding **why the system fails**.

Potential error categories include:

### Recognition Errors

The handwriting is incorrectly transcribed.

### Semantic Errors

The system incorrectly interprets the student's meaning.

### Rubric Errors

A valid concept is present but is not correctly mapped to a marking point.

### Reasoning Errors

The system identifies relevant terminology but fails to understand an incorrect logical relationship.

### Over-Marking

The system awards marks when the response does not satisfy the required criterion.

### Under-Marking

The system fails to recognize a valid alternative explanation.

### Confidence Errors

The system is highly confident despite being incorrect.

Error analysis will be used to determine where improvements are actually necessary rather than optimizing only for a single aggregate score.

---

## Scope

The initial research scope focuses on structured STEM examinations, particularly:

- Physics
- Chemistry
- Mathematics

The framework is designed around examinations with defined marking schemes and marks allocated to specific concepts, steps, or reasoning.

Expansion to additional subjects would require separate evaluation rather than assuming that a model validated on STEM responses will generalize automatically.

---

## Ethical Considerations

Automated examination assessment has direct implications for fairness.

EvalAI therefore treats automated scoring as **decision support rather than autonomous judgment**.

Key considerations include:

- Student privacy
- Bias in handwriting recognition
- Accessibility
- Language variation
- Different valid answer formulations
- Transparency of scoring
- Secure handling of examination data
- Human oversight

The system should not penalize a student simply because their handwriting or wording differs from the examples used during development.

---

## Limitations

EvalAI currently has several limitations:

1. Handwriting recognition can introduce downstream errors.
2. Scientific and mathematical notation can be difficult to interpret.
3. Semantic similarity does not automatically establish conceptual correctness.
4. Marking schemes can contain implicit teacher judgment that is difficult to formalize.
5. Human grading itself can vary between evaluators.
6. Small datasets may not represent the full diversity of student responses.
7. Automated assessment should not be assumed to generalize across subjects without independent evaluation.
8. A prototype interface does not by itself demonstrate that the underlying AI is accurate.

These limitations are part of the research problem rather than being hidden from the system design.

---

## Current Status

### Completed

- [x] Problem definition
- [x] Research question
- [x] Initial literature review
- [x] System concept
- [x] Assessment workflow
- [x] Initial prototype

### In Development

- [ ] Full multimodal model integration
- [ ] Dataset construction
- [ ] Human-annotated evaluation dataset
- [ ] Baseline experiments
- [ ] OCR/HTR benchmarking
- [ ] Semantic evaluation benchmarking
- [ ] Confidence calibration
- [ ] Human-vs-AI evaluation
- [ ] Full custom implementation

---

## Future Work

Future versions of EvalAI may investigate:

- Vision-language models for multimodal assessment
- Mathematical expression recognition
- Diagram understanding
- Question-aware grading
- Rubric generation and validation
- Confidence calibration
- Active learning from teacher corrections
- Teacher dashboards
- Large-scale human evaluation
- Cross-subject generalization
- Reproducible benchmarking
- A full Python-based ML implementation

---

## Repository Structure

The repository is intended to evolve toward:

```text
EvalAI/
│
├── README.md
│
├── docs/
│   ├── research-proposal.md
│   ├── system-architecture.md
│   ├── methodology.md
│   └── literature-review.md
│
├── src/
│   ├── preprocessing/
│   ├── ocr/
│   ├── semantic_evaluation/
│   ├── rubric/
│   ├── confidence/
│   └── explainability/
│
├── data/
│   └── README.md
│
├── experiments/
│   ├── baselines/
│   └── evaluation/
│
├── results/
│
├── assets/
│   └── screenshots/
│
├── requirements.txt
│
└── LICENSE
```

The repository structure will evolve as the project moves from prototype development toward reproducible research.

---

## Project Direction

EvalAI is ultimately built around a distinction:

```text
Automation ≠ Understanding
```

A useful assessment system should not simply ask:

> **"Did the student use the expected words?"**

It should move toward:

> **"Did the student's response demonstrate the concepts required by the marking scheme?"**

And when the answer is unclear:

> **"Should the system make this decision at all?"**

That final question is central to the project.

EvalAI therefore explores not only **how much assessment can be automated**, but **where automation should stop**.

---

## Author

**Gianna Binesh**

Student researcher interested in:

- Artificial Intelligence
- Multimodal AI
- Natural Language Processing
- Robotics
- Intelligent Systems
- Human-AI Interaction
- Educational Technology

---

## Acknowledgements

EvalAI is being developed as an independent research and engineering project exploring practical applications of AI in educational assessment.

---

## License

License information will be added as the project moves toward a reproducible public implementation.

---

## Disclaimer

EvalAI is a research project and prototype.

It is **not intended to replace qualified teachers or official examination evaluation systems**.

Automated outputs should be treated as assistive assessments and subject to human review, particularly for ambiguous or low-confidence responses.
"""
