# CENG350 — Software Engineering

METU Computer Engineering, 2024–2025 Spring. A term-long, two-person
specification-and-architecture project for the **Koster Seafloor Observatory
(KSO)** — a real marine-biodiversity platform that finds species in seafloor
video using machine learning and citizen science.

No code. The deliverable *is* the documents: something a team who has never seen
the system could build from.

## The documents

| | Pages | What's in it |
|---|---|---|
| [SRS](PROJECT%20DOCUMENT/SRS.pdf) | 68 | Software Requirements Specification — stakeholders, use cases, functional and non-functional requirements, the domain model, and the behavioural models |
| [SAD](PROJECT%20DOCUMENT/Project.pdf) | 74 | Software Architecture Description — six subsystems, their interfaces, the deployment view, and the rationale for each decision |

## The system

Volunteers annotate seafloor footage on Zooniverse; those annotations retrain the
detection models; the trained models run over new footage on HPC; and the
resulting species observations flow out to the global biodiversity databases
(GBIF, OBIS) in **Darwin Core** format. It closes a loop: more human annotation
→ better models → more observations → more footage worth annotating.

The architecture splits that into six subsystems — a researcher-facing web UI,
data management, the citizen-science bridge, a model API, and a YOLO-based
detection pipeline trained on HPC — and the SAD is mostly about the interfaces
*between* them, since that's where such a system actually fails.

## [UML/](UML)

The StarUML (`.mdj`) sources behind every diagram in the two documents, so they
can be edited rather than re-drawn.

- [`UML/SRS/`](UML/SRS) — `context.mdj` and `new_context.mdj` (the original and
  revised context diagrams), and `behaviour_diagrams.mdj`, one StarUML project
  holding the rest: the annotate-footage sequence, the model-training and
  report-generation activity diagrams, and the state machines for
  endangered-species alerts and invasive-species detection.
- [`UML/SAD/`](UML/SAD) — the package decomposition, the internal-interface class
  diagram, the model training pipeline, and the deployment diagram (each with the
  revised version produced after review feedback).

Joint work with Alper Mehmet Çelebi.
