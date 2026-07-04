Project 4 — Size the AI Estate
Student: Mohammed Imad Uddin
Student ID: F00611260

========================================================
OVERVIEW
========================================================

This project calculates Storage and Compute for an Application
for an AI estate comprising of model weights, vector database,
RAG corpus, fine-tuning datasets, logs and scratch space.

It also categorizes data into different tiers (hot, warm, cold).
and sets out a governance policy.

========================================================
FILES INCLUDED
========================================================

- data_classification.yaml   → storage policy and retention rules
- estate_sizer.py            → sizing calculator for models & vectors
- pgvector_setup.sql         → vector DB setup reference (not executed for Normal Tier)
- storage_audit.sh           → system storage audit tool
- SIZING.txt                 → manual sizing and architecture decisions
- REPORT.docx                → full written analysis report

========================================================
HOW TO RUN (VALIDATION STEPS)
========================================================

1. Run model and vector sizing check:
   python3 estate_sizer.py | tee output/estate_sizer_output.txt

2. Run storage audit:
   bash storage_audit.sh /home/ubuntu/project-04-F00611260 | tee output/storage_audit_output.txt

3. Review outputs in:
   output/estate_sizer_output.txt
   output/storage_audit_output.txt

========================================================
KEY DESIGN DECISIONS
========================================================

- INT4 quantization chosen for efficiency of the models.
- The halfvec feature was chosen for optimising the vector store.
- A primary deployment target was selected to be the 13B model.
- 70B model has been thought of but doesn't require as much VRAM headroom.
- Takes advantage of storage tiering for different latency needs.

========================================================
TIER SUMMARY
========================================================

Hot:
- Model weights
- Vector index

Warm:
- RAG corpus
- Fine-tuning dataset
- Scratch embeddings

Cold:
- Raw logs

========================================================
AI USAGE STATEMENT
========================================================

All calculations have been done manually initially.
All AI tools used were for reviewing and formatting.
Final decisions are based upon course material and human-verified.