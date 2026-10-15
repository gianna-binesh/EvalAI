# EvalAI

### Design and Evaluation of an Intelligent Assessment Framework for Handwritten Examination Responses

> **EvalAI** is a research-oriented intelligent assessment framework
> designed to evaluate handwritten examination responses using
> multimodal AI, semantic evaluation, explainable scoring, and
> human-in-the-loop review.

------------------------------------------------------------------------

## Overview

Traditional examination evaluation relies heavily on manual marking.
While human evaluation provides contextual understanding, it is
time-consuming and can introduce inconsistencies, particularly when
teachers have to process large volumes of handwritten scripts.

Digital examination workflows can improve efficiency, but simply
converting handwritten answers into text and matching keywords does not
solve the underlying problem: **understanding whether a student's
response demonstrates the knowledge required by a marking scheme.**

EvalAI explores whether multimodal AI can assist with this process.

The project investigates a pipeline that combines:

-   Handwritten text recognition
-   Image preprocessing
-   Semantic understanding of student responses
-   Marking-scheme and rubric alignment
-   Explainable scoring
-   Confidence and uncertainty estimation
-   Human-in-the-loop teacher review

The objective is **not to replace teachers**. Instead, EvalAI is
designed as a decision-support system where AI performs an initial
assessment and teachers retain final authority.

------------------------------------------------------------------------

## Problem Statement

Handwritten examination evaluation presents several challenges:

1.  **Handwriting variability** makes automated text extraction
    difficult.
2.  **OCR errors** can alter the meaning of scientific and mathematical
    responses.
3.  Correct answers may be expressed using wording that differs from the
    official marking scheme.
4.  Keyword matching can fail when students use valid alternative
    explanations.
5.  AI-generated scores without explanations are difficult for teachers
    to trust.
6.  Ambiguous or low-confidence responses require human review.
7.  Manual evaluation of large examination cohorts is time-intensive.

EvalAI investigates whether a multimodal assessment pipeline can address
these limitations while maintaining transparency and teacher oversight.

------------------------------------------------------------------------

## Research Question

> **Can a multimodal AI-based assessment framework reliably evaluate
> handwritten STEM examination responses under CBSE-style marking
> schemes compared with human teachers?**

### Supporting Questions

-   How accurately can handwritten examination responses be converted
    into machine-readable representations?
-   How does OCR/HTR error affect downstream semantic evaluation?
-   Can semantic similarity outperform exact keyword matching for
    evaluating valid alternative responses?
-   Can marking schemes and rubrics be incorporated into automated
    assessment?
-   Can confidence estimation identify responses that require teacher
    review?
-   Can explainable outputs make AI-assisted marking more interpretable
    to teachers?

------------------------------------------------------------------------

## Research Hypothesis

A multimodal AI assessment pipeline that combines handwriting
recognition, semantic representation, rubric-based evaluation, and
uncertainty estimation will provide more contextually meaningful
assessment than simple keyword or exact-match approaches, while
human-in-the-loop review will remain necessary for ambiguous or
low-confidence responses.

------------------------------------------------------------------------

## Core Philosophy

EvalAI follows four principles:

### 1. Accuracy First

The system should prioritize reliable assessment over maximum
automation.

### 2. Explainability

A score should be accompanied by reasoning that indicates how the
response aligned with the marking criteria.

### 3. Human-in-the-Loop

Teachers remain the final authority. The system should flag uncertain
cases rather than force an unreliable decision.

### 4. Fairness

The framework should evaluate the **content and reasoning of an
answer**, rather than penalizing students simply because their wording
differs from the reference answer.

------------------------------------------------------------------------

## Proposed Pipeline

``` text
                 Student Answer Sheet
                         │
                         ▼
              ┌─────────────────────┐
              │ Image Preprocessing │
              │  OpenCV / Cleaning  │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Handwriting / OCR   │
              │      Recognition    │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Structured Response │
              │    Representation   │
              └──────────┬──────────┘
                         │
             ┌───────────┴───────────┐
             ▼                       ▼
     Student Response          Marking Scheme
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
              │ Score + Explanation │
              │ + Confidence Score  │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Teacher Review      │
              │ / Final Authority   │
              └─────────────────────┘
```

------------------------------------------------------------------------

## Proposed Technology Stack

  Component                 Proposed Technology
  ------------------------- ------------------------------------------------
  Frontend / Prototype      Base44
  Image Processing          OpenCV
  Handwriting Recognition   TrOCR / HTR models
  OCR                       OCR/HTR pipeline
  Semantic Representation   Sentence-BERT / transformer embeddings
  Semantic Evaluation       Embedding similarity + rubric-based evaluation
  Explainability            Evidence-based scoring explanations
  Confidence                Model confidence + uncertainty thresholds
  Version Control           Git / GitHub
  Evaluation                Human-annotated examination responses

> **Note:** The current prototype was developed using Base44. The
> research architecture is designed to be transferable to a conventional
> Python/ML implementation as the project develops.

------------------------------------------------------------------------

## Why Semantic Evaluation?

A major limitation of traditional automated marking is reliance on exact
words.

For example, a marking scheme may expect an idea such as:

> Increasing temperature increases the kinetic energy of particles.

A student might express the same concept using different wording.

A keyword-based system may incorrectly treat the response as incorrect
if the expected words are absent.

EvalAI instead explores **semantic alignment** between:

-   the student's response,
-   the expected concept,
-   the marking criteria,
-   and the evidence contained within the answer.

This allows the system to distinguish between:

``` text
Different wording
        ≠
Different meaning
```

------------------------------------------------------------------------

## Multimodal AI Component

EvalAI is intended to operate on more than plain text.

A handwritten examination response contains multiple forms of
information:

-   Visual information
-   Handwriting structure
-   Textual content
-   Mathematical notation
-   Diagrams
-   Equations
-   Spatial relationships
-   Marking-scheme requirements

This makes examination assessment a naturally multimodal problem.

The long-term objective is therefore to move beyond a simple:

``` text
Image → OCR → Keyword Match → Score
```

pipeline toward:

``` text
Image
  ↓
Visual + Textual Understanding
  ↓
Structured Response
  ↓
Concept / Reasoning Evaluation
  ↓
Rubric Alignment
  ↓
Score + Evidence + Confidence
```

------------------------------------------------------------------------

## Scope

The initial research scope focuses on **STEM examination responses**,
particularly:

-   Physics
-   Chemistry
-   Mathematics

The framework is intended for structured examinations with defined
marking schemes and marks allocated to specific concepts, steps, or
reasoning.

------------------------------------------------------------------------

## Evaluation Framework

EvalAI will be evaluated against human assessment rather than simply
measuring whether an AI model produces a plausible answer.

Potential evaluation dimensions include:

### OCR / HTR

-   Character Error Rate (CER)
-   Word Error Rate (WER)
-   Recognition accuracy

### Assessment

-   Exact agreement with teacher-assigned marks
-   Mean Absolute Error (MAE)
-   Root Mean Square Error (RMSE)
-   Correlation with human scores
-   Agreement within an acceptable mark range

### Classification / Decision Quality

-   Precision
-   Recall
-   F1-score
-   Accuracy

### Human-in-the-Loop

-   Percentage of responses automatically accepted
-   Percentage flagged for review
-   Performance on flagged vs. non-flagged responses
-   Teacher agreement with AI explanations

------------------------------------------------------------------------

## Baselines

To determine whether the proposed framework provides meaningful
improvement, it can be compared against progressively more sophisticated
approaches:

### Baseline 1 --- Exact Matching

Checks whether expected words or phrases appear in the response.

### Baseline 2 --- Keyword-Based Matching

Uses predefined keywords associated with marking-scheme points.

### Baseline 3 --- Semantic Similarity

Uses transformer embeddings to compare student and reference responses.

### Baseline 4 --- Rubric-Aware Semantic Evaluation

Evaluates individual marking points using semantic similarity and rubric
constraints.

### Proposed System

Combines:

-   Handwriting recognition
-   Semantic evaluation
-   Rubric alignment
-   Explainability
-   Confidence estimation
-   Human review

------------------------------------------------------------------------

## Explainability

A central objective of EvalAI is to avoid producing unexplained scores.

Instead of:

``` text
Score: 2/3
```

the system should aim to produce an assessment such as:

``` text
Score: 2/3

Identified:
✓ Correct definition
✓ Correct relationship between variables

Missing:
✗ Required explanation of the physical mechanism

Confidence: High
```

This gives teachers evidence that can be reviewed rather than requiring
them to blindly trust an automated score.

------------------------------------------------------------------------

## Confidence and Uncertainty

Not every response should be automatically assessed.

The system should identify situations such as:

-   Poor handwriting recognition
-   Missing or unreadable text
-   Conflicting semantic signals
-   Answers outside the expected conceptual scope
-   Ambiguous reasoning
-   Diagrams requiring interpretation
-   Low model confidence

These responses can be routed to a teacher.

``` text
High confidence
      ↓
AI assessment → Teacher confirmation

Low confidence
      ↓
Teacher review required
```

The goal is therefore **selective automation**, not blind automation.

------------------------------------------------------------------------

## Current Prototype

The current EvalAI prototype was developed using **Base44** to rapidly
validate the product concept and assessment workflow.

The prototype focuses on demonstrating the user-facing assessment
experience before investing in a full custom ML infrastructure.

This allows the research to separate two questions:

1.  **Does the proposed assessment workflow solve a meaningful
    problem?**
2.  **Can the underlying AI pipeline achieve sufficient reliability?**

The current prototype primarily addresses the first question while
providing a foundation for subsequent technical implementation and
experimentation.

------------------------------------------------------------------------

## Project Status

### Current

-   [x] Problem definition
-   [x] Research question formulation
-   [x] Initial literature review
-   [x] Initial system concept
-   [x] Prototype development
-   [x] Initial assessment workflow
-   [ ] Full multimodal model integration
-   [ ] Dataset construction
-   [ ] Human-annotated evaluation dataset
-   [ ] Baseline experiments
-   [ ] OCR/HTR benchmarking
-   [ ] Semantic evaluation benchmarking
-   [ ] Confidence calibration
-   [ ] Human-vs-AI evaluation
-   [ ] Full custom implementation

------------------------------------------------------------------------

## Research Workflow

``` text
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

------------------------------------------------------------------------

## Dataset

The intended evaluation dataset will consist of handwritten examination
responses paired with:

-   Question
-   Student response
-   Reference answer
-   Marking scheme
-   Human-assigned score
-   Relevant marking points
-   Optional teacher comments
-   AI-generated score
-   AI confidence
-   AI explanation

A key requirement is that evaluation data should preserve the
distinction between **correctness of content** and **surface-level
wording**.

------------------------------------------------------------------------

## Error Analysis

An important part of the project is understanding **why** the system
fails.

Potential error categories include:

### Recognition Errors

The handwritten response is incorrectly transcribed.

### Semantic Errors

The system incorrectly interprets the student's meaning.

### Rubric Errors

The response contains a valid concept that is not correctly mapped to a
marking point.

### Reasoning Errors

The system identifies relevant keywords but fails to understand an
incorrect logical relationship.

### Over-Marking

The system awards marks for an answer that does not fully satisfy the
rubric.

### Under-Marking

The system fails to recognize a valid alternative explanation.

### Uncertainty Errors

The system is highly confident despite being incorrect.

These categories can help identify where improvements are needed.

------------------------------------------------------------------------

## Ethical Considerations

AI-assisted examination assessment has significant fairness
implications.

EvalAI therefore treats automated scoring as **decision support rather
than autonomous judgment**.

Important considerations include:

-   Student privacy
-   Bias in handwriting recognition
-   Accessibility
-   Language variation
-   Different valid answer formulations
-   Transparency of scoring
-   Human oversight
-   Secure handling of examination data

The system should not penalize a student merely because their
handwriting or wording differs from the data used to develop the model.

------------------------------------------------------------------------

## Limitations

The project currently has several limitations:

1.  Handwriting recognition can introduce downstream errors.
2.  Scientific and mathematical notation is more difficult to interpret
    than ordinary text.
3.  Semantic similarity does not automatically imply conceptual
    correctness.
4.  A marking scheme may contain implicit teacher judgment that is
    difficult to formalize.
5.  Human grading itself can vary between evaluators.
6.  A small dataset may not represent the full diversity of student
    responses.
7.  Automated assessment should not be assumed to generalize across
    subjects without evaluation.

These limitations are part of the research problem rather than being
hidden from the system design.

------------------------------------------------------------------------

## Future Work

Future versions of EvalAI may explore:

-   Advanced multimodal vision-language models
-   Better mathematical expression recognition
-   Diagram understanding
-   Question-aware grading
-   Rubric generation and validation
-   Calibration of confidence scores
-   Active learning from teacher corrections
-   Personalized error analysis
-   Large-scale human evaluation
-   Cross-subject generalization
-   Teacher dashboards
-   Dataset expansion
-   Full Python-based ML infrastructure
-   Reproducible benchmarking

------------------------------------------------------------------------

## Repository Structure

The repository is intended to evolve toward the following structure:

``` text
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

> The current repository may not contain all of these directories yet.
> They represent the intended development structure as the research
> implementation progresses.

------------------------------------------------------------------------

## Prototype

The current prototype was built using Base44.

**Prototype:** [EvalAI Base44
Prototype](https://grinning-eval-grade-flow.base44.app/)

The prototype is intended as a proof-of-concept interface and does not
represent the final research implementation.

------------------------------------------------------------------------

## Research Direction

EvalAI is ultimately intended to investigate a broader question:

> **Can AI assist with evaluating not just what a student wrote, but
> what the student demonstrated they understood?**

The distinction is important.

A robust assessment system should move beyond:

``` text
"Did the student use the expected words?"
```

toward:

``` text
"Did the student's response demonstrate the concepts
required by the marking scheme?"
```

That is the central research direction behind EvalAI.

------------------------------------------------------------------------

## Author

**Gianna Binesh**

Student researcher interested in:

-   Artificial Intelligence
-   Multimodal AI
-   Natural Language Processing
-   Robotics
-   Intelligent Systems
-   Human-AI Interaction
-   Educational Technology

------------------------------------------------------------------------

## Acknowledgements

This project is being developed as an independent research and
engineering project, with the aim of exploring practical applications of
AI in educational assessment.

------------------------------------------------------------------------

## License

License information will be added as the project moves toward a
reproducible public implementation.

------------------------------------------------------------------------

## Disclaimer

EvalAI is a research project and prototype.

It is **not intended to replace qualified teachers or official
examination evaluation systems**. Any automated score should be treated
as an assistive assessment and subject to human review, particularly for
ambiguous or low-confidence responses.
